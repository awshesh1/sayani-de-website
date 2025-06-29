# AWS Deployment Guide for Sayani De Author Website

## Prerequisites
- AWS Account
- Node.js 18+ installed locally
- Git installed

## Deployment Options

### Option 1: AWS Amplify (Recommended - Easiest)

1. **Prepare the code:**
   - Download all files from this Replit project
   - Replace `package.json` with `package-aws.json` (rename it to `package.json`)
   - Create a new GitHub repository
   - Upload all files to GitHub

2. **Deploy on AWS Amplify:**
   - Go to AWS Amplify Console
   - Click "New App" → "Host web app"
   - Connect your GitHub repository
   - Amplify will auto-detect the build settings
   - Add environment variables:
     - `GMAIL_USER` = your Gmail address
     - `GMAIL_PASS` = your Gmail app password
     - `WRITER_EMAIL` = sayanide1984@gmail.com
   - Deploy!

### Option 2: AWS EC2 (More Control)

1. **Launch EC2 Instance:**
   - Choose Ubuntu 22.04 LTS
   - t2.micro (free tier eligible)
   - Configure security group: Allow HTTP (80), HTTPS (443), SSH (22)

2. **Setup on EC2:**
   ```bash
   # Connect to your instance
   ssh -i your-key.pem ubuntu@your-ec2-ip
   
   # Install Node.js
   curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
   sudo apt-get install -y nodejs
   
   # Install PM2 for process management
   sudo npm install -g pm2
   
   # Upload your code (use scp or git clone)
   git clone your-github-repo
   cd your-repo
   
   # Install dependencies
   npm install
   
   # Build the application
   npm run build
   
   # Set environment variables
   export GMAIL_USER="your-gmail"
   export GMAIL_PASS="your-app-password"
   export WRITER_EMAIL="sayanide1984@gmail.com"
   export NODE_ENV="production"
   
   # Start with PM2
   pm2 start dist/server.js --name "sayani-website"
   pm2 startup
   pm2 save
   ```

3. **Setup Nginx (Optional - for custom domain):**
   ```bash
   sudo apt install nginx
   sudo nano /etc/nginx/sites-available/default
   ```
   
   Add this configuration:
   ```nginx
   server {
       listen 80;
       server_name your-domain.com;
       
       location / {
           proxy_pass http://localhost:5000;
           proxy_http_version 1.1;
           proxy_set_header Upgrade $http_upgrade;
           proxy_set_header Connection 'upgrade';
           proxy_set_header Host $host;
           proxy_cache_bypass $http_upgrade;
       }
   }
   ```

### Option 3: AWS Elastic Beanstalk

1. **Prepare deployment package:**
   - Create a zip file with all your code
   - Include the `package-aws.json` (renamed to `package.json`)

2. **Deploy on Elastic Beanstalk:**
   - Go to Elastic Beanstalk Console
   - Create new application
   - Choose "Node.js" platform
   - Upload your zip file
   - Configure environment variables in Configuration → Software

## Environment Variables Required

Set these on your chosen AWS platform:

```
GMAIL_USER=your-gmail-address
GMAIL_PASS=your-gmail-app-password
WRITER_EMAIL=sayanide1984@gmail.com
NODE_ENV=production
PORT=5000 (or whatever port AWS assigns)
```

## Cost Estimates (Monthly)

- **AWS Amplify**: ~$1-5 for small sites
- **EC2 t2.micro**: Free tier for 12 months, then ~$8-10/month
- **Elastic Beanstalk**: ~$10-20/month

## Post-Deployment

1. Test the contact form to ensure emails are working
2. Check all social media links
3. Verify all published story links work
4. Test responsive design on mobile devices

## Custom Domain (Optional)

To use your own domain (e.g., sayanide.com):
1. Purchase domain from Route 53 or external provider
2. Configure DNS settings in your chosen AWS service
3. Set up SSL certificate (AWS Certificate Manager for free SSL)

## Updating the Site

After deployment, to make changes:
1. Update your code locally or in GitHub
2. Redeploy using your chosen method:
   - Amplify: Push to GitHub (auto-deploys)
   - EC2: Pull changes and restart PM2
   - Elastic Beanstalk: Upload new zip file

Your website will be live and accessible worldwide once deployed!