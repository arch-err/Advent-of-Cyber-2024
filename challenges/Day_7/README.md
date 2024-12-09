# Day_7
*Log analysis using cli-tools. Yay!!*


1. ***What is the other activity made by the user glitch aside from the ListObject action?***
- **Answer:** `PutObject`
> **Solution:** `cat cloudtrail_log.json | jq ".Records[] | select( .userIdentity.userName == \"glitch\" ) | .eventName" | bat`

2. ***What is the source IP related to the S3 bucket activities of the user glitch?***
- **Answer:** `53.94.201.69`
> **Solution:** `cat cloudtrail_log.json | jq ".Records[] | select( .userIdentity.userName == \"glitch\" ) | select( .eventName | endswith(\"Bucket\")) | .sourceIPAddress"`

3. ***Based on the eventSource field, what AWS service generates the ConsoleLogin event?***
- **Answer:** `signin.amazonaws.com`
> **Solution:** `cat cloudtrail_log.json | jq ".Records[] | select( .eventName == \"ConsoleLogin\" ) | .eventSource" | sort | uniq`

4. ***When did the anomalous user trigger the ConsoleLogin event?***
- **Answer:** `2024-11-28T15:21:54Z`
> **Solution:** `cat cloudtrail_log.json | jq ".Records[] | select( .eventName == \"ConsoleLogin\" ) | select(.userIdentity.userName == \"glitch\") | .eventTime"`

5. ***What was the name of the user that was created by the mcskidy user?***
- **Answer:** `glitch`
> **Solution:** `cat cloudtrail_log.json | jq ".Records[] | select( .eventName == \"CreateUser\") | select( .userIdentity.userName == \"mcskidy\") | .responseElements.user.userName"`

6. ***What type of access was assigned to the anomalous user?***
- **Answer:** `AdministratorAccess`
> **Solution:** `cat cloudtrail_log.json | jq ".Records[] | select( .eventName == \"AttachUserPolicy\") | select( .userIdentity.userName == \"mcskidy\") | .requestParameters.policyArn"`

7. ***Which IP does Mayor Malware typically use to log into AWS?***
- **Answer:** `53.94.201.69`
> **Solution:** `cat cloudtrail_log.json | jq ".Records[] | select( .userIdentity.userName == \"mayor_malware\" ) | .sourceIPAddress" | sort | uniq`

8. ***What is McSkidy's actual IP address?***
- **Answer:** `31.210.15.79`
> **Solution:** `cat cloudtrail_log.json | jq ".Records[] | select( .userIdentity.userName == \"mcskidy\" ) | .sourceIPAddress" | sort | uniq | grep -v "53."`

9. ***What is the bank account number owned by Mayor Malware?***
- **Answer:** `2394 6912 7723 1294`
> **Solution:** `cat rds.log | grep "Mayor" | tail -1`
