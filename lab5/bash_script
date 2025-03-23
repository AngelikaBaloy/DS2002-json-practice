#!/Users/angelikabaloy/DS2002-json-practice/lab5

# fetch data 
curl -s "https://aviationweather.gov/api/data/metar?ids=KMCI&format=json&taf=false&hours=12&bbox=40%2C-90%2C45%2C-85" > aviation.json

# first six receiptTime values
jq -r '.[0:6] | .[].receiptTime' aviation.json 

# average temperature from last twelve hours  
temps=$(jq -r '.[0:12] | .[].temp' aviation.json) 

sum=0

while IFS= read -r temp; do 
    sum=$(echo "$sum + $temp" | bc -l )
done <<< "$temps"
 
avg_temp=$(echo "scale=2; $sum / 12"| bc -l)
echo "Average Temperature: $avg_temp" 

# cloud value 
clouds=$(jq -r '.[0:12] | .[].clouds[].cover' aviation.json)

clear=0

for cloud in $clouds; do 
    if [ "$cloud" = "CLR" ]; then 
        clear=$((clear + 1))
    fi
done 

if [ "$clear" -ge 6 ]; then 
    echo "Mostly Cloudy: false" 
else 
    echo "Mostly Cloudy: true" 
fi


