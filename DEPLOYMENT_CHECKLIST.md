1. Verify Backend Requirements
# requirements.txt is in ROOT directory (not backend/)
cat requirements.txt | grep gunicorn
If gunicorn is not there, it should be added (already done).

2. Test Build Locally (Optional)
# Build Docker image
docker build -t shark-api .

# Run it
docker run -p 8000:8000 \
  -e MONGO_CONNECTION_STRING="mongodb+srv://..." \
  shark-api
3. Commit All Changes
git add .
git commit -m "Setup for free deployment on Render + Vercel"
git push origin main
4. Have These Ready
 MongoDB Atlas connection string
 GitHub repository created and pushed
 Render account (create at render.com)
 Vercel account (create at vercel.com)
Deployment Order (Do in this order)
Backend first - Deploy on Render

Get backend URL: https://shark-api-xxxxx.onrender.com
Wait for success (2-3 min)
Frontend second - Deploy on Vercel

Add backend URL as VITE_API_URL environment variable
Deploy (1-2 min)
Test - Open frontend and verify connection

After Deployment
Update Keep-Alive Workflow
Edit .github/workflows/keep-alive.yml:

Replace https://shark-api-xxxxx.onrender.com with your actual backend URL
Monitor Services
Render Dashboard: https://dashboard.render.com
Vercel Dashboard: https://vercel.com/dashboard
Check logs if something goes wrong
Support Resources
docs/FREE_DEPLOYMENT.md - Detailed free deployment guide
docs/DEPLOYMENT_GUIDE.md - All deployment options
Render Docs: https://render.com/docs
Vercel Docs: https://vercel.com/docs
MongoDB Atlas: https://www.mongodb.com/docs/atlas/
Quick Reference URLs
After deployment, your URLs will be:

Frontend: https://shark-foraging-XXXXX.vercel.app
Backend: https://shark-api-XXXXX.onrender.com
API Docs: https://shark-api-XXXXX.onrender.com/docs
Health Check: https://shark-api-XXXXX.onrender.com/health
