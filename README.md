# Titanic
Kaggle Project
# Read the data from the source

train=read.csv(file.choose())
head(train)
dim(train)

# See which variables are important

t.glm=glm(Survived~., data = train)
summary(t.glm)
# Extract the variables that are important for our prediction

train1=train[,c(2,3,5,6,7)]
head(train1)
t.glm=glm(Survived~., data = train1)
summary(t.glm) #We can use t.glm to predict test data

# Load test data
test=read.csv(file.choose())
dim(test1)

# Extract the variables that are important for our prediction
test1=test[,c(2,4,5,6)]
pred=predict.glm(t.lm,test1,family='Binomial', type = 'response')
# convert NA's to 0
pred[is.na(pred)]=0

# Convert probabilities to binary (0-1)
pred[pred>=0.5]=1
pred[pred<0.5]=0

# Write the result
write.csv(pred,'predtitanic.csv')

