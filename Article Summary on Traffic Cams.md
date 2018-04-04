# Article-Summary

Article Summary Assignment for Stats
1) DOWNLOAD: http://www.mediafire.com/file/hj8jxkd2hw4m89a/trafficcameras.csv
2) ADD .CSV FILE TO "myData = read.csv("")"

myData = read.csv("")

myData

head(myData)
Lat = myData$LATITUDE
Rot = myData$ROTATION

hist(Lat)
hist(Rot)


nLat = length(Lat)
nRot = length(Rot)
dfLat = nLat-1
dfRot = nRot-1
df_total = dfLat+dfRot
meanLat = sum(Lat)/nLat
meanRot = sum(Rot)/nRot
mean_diff = meanRot - meanLat
centeredLat = Lat - meanLat
centeredRot = Rot - meanRot
ssLat = sum(centeredLat^2)
ssRot = sum(centeredRot^2)
vLat = ssLat/dfLat
vRot = ssRot/dfRot
vp = (ssLat+ssRot)/(dfLat+dfRot)
se_p = sqrt(vp/nLat + vp/nRot)
t = mean_diff/se_p
t

dscore = Lat - Rot
dscore
dsquare = dscore^2
dsquare
dscoresum = sum(dscore)
dscoresum
dsquaresum = sum(dsquare)
dsquaresum

mDiff = dscoresum/nLat
ss = dsquaresum - ((dscoresum)^2/nLat)
ss
v = ss/dfLat ##s^2 or sample variance
se = sqrt(v/nLat) ##Standard error
v
se
se_p
trep = mDiff/se ##t-test for repeated measures data
trep

listofmeans = c(Lat,Rot)
listofsem = c(se,se)

midpoints = barplot(listofmeans, main = "Latitude & Rotation on Traffic Cam", xlab = "Latitude",ylab = "Rotation in Degrees", ylim = c(0,400))
arrows(
  midpoints, listofmeans-listofsem, ##Start point of lines
  midpoints, listofmeans+listofsem, ##End point of lines
  length=0.05,angle=90,code=3,
)

Fmax = vRot/vLat
Fmax


