# by default release on  Lenovo xCAT BR 17E ,we don't support nvme drive 
# here is an update to support [jarrod johnson's update ](https://github.com/jjohnson42/xcat-core/commit/3df67da101547ab2f9c52864dd75f2fb2f302e55)
```
37 37    
38 38      # Get all partitions and disks from /proc/partitions file  
39 39      if [ -z "$has_awk" ]; then  
40  -        entries=$(cat /proc/partitions | sed 's/  */ /g' | cut -d " " -f5 | grep -v "name" | grep -e "[s|h|v]d.*$")  
 40 +        entries=$(cat /proc/partitions | sed 's/  */ /g' | cut -d " " -f5 | grep -v "name" | grep -E '^[s|h|v]d|nvme')  
41 41      else  
42  -        entries=$(awk -F ' '  '{print $4}' /proc/partitions | grep -v "name" | grep -e "[s|h|v]d.*$")  
 42 +        entries=$(awk -F ' '  '{print $4}' /proc/partitions | grep -v "name" | grep -E '^[s|h|v]d|nvme')  
43 43      fi      
44 44    
45 45      # Classify entries by DEVTYPE  
46 46      for entry in $entries; do  
 47 +        DEVSIZE=$(udevadm info --attribute-walk --name=$entry|grep size| sed -e 's/[^"]*"//' -e 's/"//'|tail -n 1)  
 48 +        if [ -z "$DEVSIZE" -o $DEVSIZE -lt 262144 ]; then  
 49 +            # ignore small devices, that are likely remote media or similar  
 50 +            continue  
 51 +        fi  
 52 +  
47 53          if [ -z "$has_awk" ]; then  
48 54              dev_type=$(udevadm info --query=property --name=/dev/$entry | grep -i "DEVTYPE" | cut -d "=" -f2 | $utolcmd)  
```

