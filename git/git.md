
''''
ssh-keygen -t rsa -b 4096 -C "example-email@gmail.com"
mv key-name* ~/.ssh/
#we have 2 files generated 
cat ~/.ssh/vinay-desktop-git.pub
eval $(ssh-agent -s)
ssh-add ~/.ssh/vinay.hpatil-git

''''
