import boto3
import sys
import os
import time
ec2 = boto3.resource ('ec2')

for instance in ec2.instances.all():
    #print (instance.id, instance.state)
     
    if (instance.state == {'Code': 16, 'Name': 'running'}):
     print ('Following instances are running')
     print ((instance.id))
     instance.stop()
     print ((instance.id) + 'Instance is stopped')
    
    else: 
     instance.start()
     print ((instance.id) + " is started")
