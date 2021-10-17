SSH into a running container:
1) Use docker ps to get the name of the existing container.
2) Use the command docker exec -it "container name" /bin/bash to get a bash shell in the container.
3) Generically, use docker exec -it "container name" "command" to execute whatever command you specify in the container.
  
  
It turned out that AppArmor service was messing up with Docker. AppArmor (or "Application Armor") is a Linux kernel security module that allows the system administrator to restrict programs' capabilities with per-program profiles. For this problem with containers, it helped me to remove the unknown from AppArmor using the following command:

sudo aa-remove-unknown

After that, I was able to stop and kill my containers. 
