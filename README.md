#1
import csv
def loadCsv(filename):
lines = csv.reader(open(filename, "rt"))
dataset = list(lines)
for i in range(len(dataset)):
dataset[i] = dataset[i]
return dataset
attributes = ['Sky','Temp','Humidity','Wind','Water','Forecast']
print(attributes)
num_attributes = len(attributes)
filename = "Weather.csv"
dataset = loadCsv(filename)
print(dataset)
target=['Yes','Yes','No','Yes']
print(target)
hypothesis=['0'] * num_attributes
print(hypothesis)
print("The Hypothesis are")
for i in range(len(target)):
 
 if(target[i] == 'Yes'):
 for j in range(num_attributes): 
 if(hypothesis[j]=='0'):
 hypothesis[j] = dataset[i][j]
 if(hypothesis[j]!= dataset[i][j]):
 hypothesis[j]='?'
 
 print(i+1,'=',hypothesis)
 
print("Final Hypothesis")
print(hypothes)
------------------------
#2
import numpy as np
import pandas as pd

data = pd.DataFrame(data=pd.read_csv('Training_examples.csv'))
concepts = np.array(data.iloc[:,0:-1])
target = np.array(data.iloc[:,-1])
def learn(concepts, target):
 specific_h = concepts[0].copy()
 print("initialization of specific_h and general_h")
 print(specific_h)
 general_h = [["?" for i in range(len(specific_h))] for i in range(len(specific_h))]
 print(general_h)

 for i, h in enumerate(concepts):
 if target[i] == "Yes":
 for x in range(len(specific_h)):
 if h[x] != specific_h[x]:
##6
 specific_h[x] = '?'
 general_h[x][x] = '?'
 if target[i] == "No":
 for x in range(len(specific_h)):
 if h[x] != specific_h[x]:
 general_h[x][x] = specific_h[x]
 else:
 general_h[x][x] = '?'
 print(" steps of Candidate Elimination Algorithm",i+1)
 print(specific_h)
 print(general_h)
 indices = [i for i, val in enumerate(general_h) if val == ['?', '?', '?', '?', '?', '?']]
 for i in indices:
 general_h.remove(['?', '?', '?', '?', '?', '?'])
 return specific_h, general_h
s_final, g_final = learn(concepts, target)
print("Final Specific_h:", s_final, sep="\n")
print("Final General_h:", g_final, sep="\n")
#3
from sklearn.datasets import fetch_20newsgroups
twenty_train = fetch_20newsgroups(subset='train', shuffle=True)
print("lenth of the twenty_train--------->", len(twenty_train))
#print(twenty_train.target_names) 
#print("\n".join(twenty_train.data[0].split("\n")[:5]))#prints first line of the first data file

from sklearn.feature_extraction.text import CountVectorizer
count_vect = CountVectorizer()
X_train_counts = count_vect.fit_transform(twenty_train.data)
print('dim=',X_train_counts.shape)
from sklearn.feature_extraction.text import TfidfTransformer
tfidf_transformer = TfidfTransformer()
X_train_tfidf = tfidf_transformer.fit_transform(X_train_counts)
print(X_train_tfidf.shape)
from sklearn.naive_bayes import MultinomialNB
clf = MultinomialNB().fit(X_train_tfidf, twenty_train.target)

from sklearn.pipeline import Pipeline
text_clf = Pipeline([('vect', CountVectorizer()), ('tfidf', TfidfTransformer()), ('clf', 
MultinomialNB())])
text_clf = text_clf.fit(twenty_train.data, twenty_train.target)

import numpy as np
twenty_test = fetch_20newsgroups(subset='test', shuffle=True)
predicted = text_clf.predict(twenty_test.data)
accuracy=np.mean(predicted == twenty_test.target)
print("Predicted Accuracy = ",accuracy)
from sklearn import metrics
print("Accuracy= ",metrics.accuracy_score(twenty_test.target,predicted))
print("Precision=",metrics.precision_score(twenty_test.target,predicted,average=None))
print("Recall=",metrics.recall_score(twenty_test.target,predicted,average=None))
print(metrics.classification_report(twenty_test.target, 
predicted,target_names=twenty_test.target_names))

-----------------------
#7
import bayespy as bp
import numpy as np
import csv 
from colorama import init
from colorama import Fore, Back, Style
init()
#Age
ageEnum = {'SuperSeniorCitizen':0, 'SeniorCitizen':1, 'MiddleAged':2, 'Youth':3, 
'Teen':4}
genderEnum = {'Male':0, 'Female':1}
familyHistoryEnum = {'Yes':0, 'No':1}
dietEnum = {'High':0, 'Medium':1, 'Low':2}
lifeStyleEnum = {'Athlete':0, 'Active':1, 'Moderate':2, 'Sedetary':3}
cholesterolEnum = {'High':0, 'BorderLine':1, 'Normal':2}
heartDiseaseEnum = {'Yes':0, 'No':1}
#heart_disease_data.csv
with open('heart_disease_data.csv') as csvfile:
 lines = csv.reader(csvfile)
 dataset = list(lines)
 data = []
 for x in dataset: 
 
data.append([ageEnum[x[0]],genderEnum[x[1]],familyHistoryEnum[x[2]],dietEnum[x[
3]],lifeStyleEnum[x[4]],cholesterolEnum[x[5]],heartDiseaseEnum[x[6]]])
data = np.array(data)
N = len(data)
p_age = bp.nodes.Dirichlet(1.0*np.ones(5))
age = bp.nodes.Categorical(p_age, plates=(N,))
age.observe(data[:,0])
p_gender = bp.nodes.Dirichlet(1.0*np.ones(2))
gender = bp.nodes.Categorical(p_gender, plates=(N,))
gender.observe(data[:,1])
p_familyhistory = bp.nodes.Dirichlet(1.0*np.ones(2))
familyhistory = bp.nodes.Categorical(p_familyhistory, plates=(N,))
familyhistory.observe(data[:,2])
p_diet = bp.nodes.Dirichlet(1.0*np.ones(3))
17
diet = bp.nodes.Categorical(p_diet, plates=(N,))
diet.observe(data[:,3])
p_lifestyle = bp.nodes.Dirichlet(1.0*np.ones(4))
lifestyle = bp.nodes.Categorical(p_lifestyle, plates=(N,))
lifestyle.observe(data[:,4])
p_cholesterol = bp.nodes.Dirichlet(1.0*np.ones(3))
cholesterol = bp.nodes.Categorical(p_cholesterol, plates=(N,))
cholesterol.observe(data[:,5])
p_heartdisease = bp.nodes.Dirichlet(np.ones(2), plates=(5, 2, 2, 3, 4, 3))
heartdisease = bp.nodes.MultiMixture([age, gender, familyhistory, diet, lifestyle, 
cholesterol], bp.nodes.Categorical, p_heartdisease)
heartdisease.observe(data[:,6])
p_heartdisease.update()
#print("Sample Probability")
#print("Probability(HeartDisease|Age=SuperSeniorCitizen, Gender=Female, 
FamilyHistory=Yes, DietIntake=Medium, LifeStyle=Sedetary, Cholesterol=High)")
#print(bp.nodes.MultiMixture([ageEnum['SuperSeniorCitizen'], genderEnum['Female'], 
familyHistoryEnum['Yes'], dietEnum['Medium'], lifeStyleEnum['Sedetary'], 
cholesterolEnum['High']], bp.nodes.Categorical, p_heartdisease).get_moments()[0]
[heartDiseaseEnum['Yes']])
m = 0
while m == 0:
 print("\n")
 res = bp.nodes.MultiMixture([int(input('Enter Age: ' + str(ageEnum))), 
int(input('Enter Gender: ' + str(genderEnum))), int(input('Enter FamilyHistory: ' + 
str(familyHistoryEnum))), int(input('Enter dietEnum: ' + str(dietEnum))), 
int(input('Enter LifeStyle: ' + str(lifeStyleEnum))), int(input('Enter Cholesterol: ' + 
str(cholesterolEnum)))], bp.nodes.Categorical, p_heartdisease).get_moments()[0]
[heartDiseaseEnum['Yes']]
 print("Probability(HeartDisease) = " + str(res))
 
#print(Style.RESET_ALL)
 
 m = int(input("Enter for Continue:0, Exit :1 "))
 -----------------------------
 ##9
from sklearn.datasets import load_iris
iris = load_iris()
print("Feature Names:",iris.feature_names,"Iris Data:",iris.data,"Target 
Names:",iris.target_names,"Target:",iris.target)
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(
 iris.data, iris.target, test_size = .25)
from sklearn.neighbors import KNeighborsClassifier
clf = KNeighborsClassifier()
clf.fit(X_train, y_train)
print(" Accuracy=",clf.score(X_test, y_test))
print("Predicted Data")
print(clf.predict(X_test))
prediction=clf.predict(X_test)
print("Test data :")
print(y_test)
diff=prediction-y_test
print("Result is ")
print(diff)
print('Total no of samples misclassied =', sum(abs(diff)))

#10
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

def kernel(point,xmat, k):
 m,n = np.shape(xmat)
 weights = np.mat(np.eye((m)))
 for j in range(m):
 diff = point - X[j]
 weights[j,j] = np.exp(diff*diff.T/(-2.0*k**2))
 return weights
def localWeight(point,xmat,ymat,k):
 wei = kernel(point,xmat,k)
 W = (X.T*(wei*X)).I*(X.T*(wei*ymat.T))
 return W
 
def localWeightRegression(xmat,ymat,k):
 m,n = np.shape(xmat)
 ypred = np.zeros(m)
 for i in range(m):
 ypred[i] = xmat[i]*localWeight(xmat[i],xmat,ymat,k)
 return ypred
data = pd.read_csv('LR.csv')
colA = np.array(data.colA)
colB = np.array(data.colB)
mcolA = np.mat(colA)
mcolB = np.mat(colB)
m= np.shape(mcolA)[1]
one = np.ones((1,m),dtype=int)
X= np.hstack((one.T,mcolA.T))
print(X.shape)
ypred = localWeightRegression(X,mcolB,0.5)
SortIndex = X[:,1].argsort(0)
xsort = X[SortIndex][:,0]
29
 
fig = plt.figure()
ax = fig.add_subplot(1,1,1)
ax.scatter(colA,colB, color='green')
ax.plot(xsort[:,1],ypred[SortIndex], color = 'red', linewidth=5)
plt.xlabel('colA')
plt.ylabel('colB')
plt.show();
