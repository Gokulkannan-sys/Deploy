# Deploy
Github Actions


name: Deploy to EC2

on:
   workflow_dispatch:    
   
jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
    # Step 1: Checkout the repository to get the code
    - name: Checkout repository
      uses: actions/checkout@v2

    - name: Deploy to EC2
      #env:
        #PRIVATE_KEY: ${{ secrets.EC2_PRIVATE_KEY }}
        #HOST: ${{ secrets.EC2_HOST }}
        #USER: ${{ secrets.EC2_USER }}
      run: |
        pwd
        ls
        chmod 400 pri.pem
        scp -o StrictHostKeyChecking=no -i /home/runner/work/deploy/deploy/pri.pem index.html ubuntu@3.84.185.49:/tmp/
        ssh -o StrictHostKeyChecking=no -i /home/runner/work/deploy/deploy/pri.pem ubuntu@3.84.185.49
