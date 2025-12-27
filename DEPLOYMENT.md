# 🚀 Streamlit Cloud Deployment Guide

## Quick Deploy to Streamlit Cloud (Recommended)

### Step 1: Sign Up for Streamlit Cloud
1. Go to [share.streamlit.io](https://share.streamlit.io)
2. Click **"Sign up"**
3. Choose **"Sign up with GitHub"**
4. Authorize Streamlit to access your GitHub account

### Step 2: Deploy Your App
1. Click **"New app"** button
2. Select your repository: `Lerato-leo/Predicting-Healthcare-insurance-cost`
3. Select branch: `main`
4. Select file: `streamlit_app.py`
5. Click **"Deploy"**

**That's it!** Streamlit will automatically:
- Install requirements from `requirements.txt`
- Build and deploy your app
- Generate a shareable URL

### Expected URL
```
https://predicting-healthcare-insurance-cost-<random>.streamlit.app
```

---

## Alternative: Docker Deployment (Advanced)

### Step 1: Create Dockerfile
Already have a Dockerfile in your repo. Build it:

```bash
docker build -t insurance-predictor .
```

### Step 2: Run Docker Container Locally
```bash
docker run -p 8501:8501 insurance-predictor
```

Access at: http://localhost:8501

### Step 3: Deploy to Cloud

#### Option A: Heroku
```bash
heroku login
heroku create your-app-name
heroku container:push web
heroku container:release web
heroku open
```

#### Option B: AWS
```bash
# Push to ECR
aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin
docker tag insurance-predictor:latest <AWS_ACCOUNT>.dkr.ecr.us-east-1.amazonaws.com/insurance:latest
docker push <AWS_ACCOUNT>.dkr.ecr.us-east-1.amazonaws.com/insurance:latest

# Deploy to ECS or Fargate
```

#### Option C: Google Cloud Run
```bash
gcloud auth login
gcloud config set project YOUR_PROJECT_ID
gcloud builds submit --tag gcr.io/YOUR_PROJECT_ID/insurance-predictor
gcloud run deploy insurance-predictor --image gcr.io/YOUR_PROJECT_ID/insurance-predictor --platform managed
```

---

## Environment Variables (For Production)

Create a `.streamlit/config.toml` file:

```toml
[client]
showErrorDetails = false
showWarningOnDirectExecution = false

[logger]
level = "warning"

[server]
port = 8501
headless = true
runOnSave = true
```

---

## Important Notes

### Database
- Currently uses SQLite (users.db) stored locally
- For production, consider:
  - PostgreSQL
  - MongoDB Atlas
  - Firebase Realtime Database

### Secrets Management
Add sensitive data via Streamlit Cloud:
1. Go to your app settings
2. Click **"Secrets"**
3. Add your configuration:

```toml
[database]
connection_string = "postgresql://user:password@host/db"

[openai]
api_key = "sk-..."
```

### Static Files
The app loads CSS from `static/style_new.css`. This is included in deployment.

---

## Monitoring & Logs

### Streamlit Cloud
- View real-time logs in the app settings
- Monitor performance metrics
- Set up email alerts for errors

### Docker/Self-Hosted
```bash
# View container logs
docker logs <container_id>

# Stream logs in real-time
docker logs -f <container_id>
```

---

## Troubleshooting

### "ModuleNotFoundError"
- Check `requirements.txt` has all dependencies
- Ensure Python 3.9+ is used

### Database Not Found
- Uses relative paths (fixed in v2.0)
- Streamlit Cloud creates persistent directory
- For SQLite alternatives, use cloud database

### Port Already in Use
```bash
# Kill process on port 8501
lsof -ti:8501 | xargs kill -9

# Or use different port
streamlit run streamlit_app.py --server.port 8502
```

### TensorFlow Warnings
These are normal and non-critical:
- `oneDNN custom operations`
- `deprecated tf.losses.sparse_softmax_cross_entropy`

They don't affect functionality.

---

## Performance Optimization

### For Production:
1. **Cache Strategy**: Add `@st.cache_resource` for expensive operations
2. **Model Optimization**: Use quantized models for faster inference
3. **Database**: Migrate to cloud database (PostgreSQL/MongoDB)
4. **CDN**: Serve static files via CloudFront/Cloudflare

---

## Security Checklist

- ✅ Password hashing (SHA256) - Already implemented
- ✅ User authentication - Already implemented
- ✅ Environment variables for secrets
- ✅ HTTPS/SSL (automatic on Streamlit Cloud)
- ✅ Rate limiting (add if needed)
- ✅ Input validation (add if needed)

---

## Recommended: Deploy on Streamlit Cloud

**Advantages:**
- ✅ Free tier available
- ✅ Automatic HTTPS
- ✅ Auto-deployment on git push
- ✅ No server management
- ✅ Built-in monitoring
- ✅ Easy secret management
- ✅ 1 free app included

**Steps (Quick):**
1. Go to https://share.streamlit.io
2. Sign in with GitHub
3. Click "New app"
4. Select repo, branch, and file
5. Deploy! 🚀

**That's all you need!**

---

## Support

For issues:
- 📖 [Streamlit Docs](https://docs.streamlit.io)
- 🐛 [GitHub Issues](https://github.com/Lerato-leo/Predicting-Healthcare-insurance-cost/issues)
- 💬 [Streamlit Community](https://discuss.streamlit.io)

