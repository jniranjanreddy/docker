# 🚀 AI Learning Notebooks

Welcome to your AI learning journey! This directory contains Jupyter notebooks to help you get started with AI and machine learning.

## 📚 Available Notebooks:

### 1. **01_AI_Getting_Started.ipynb**
- Basic introduction to AI and machine learning
- Data manipulation with pandas
- Building your first ML model
- Using MLflow for experiment tracking

### 2. **02_Data_Analysis_with_Kafka.ipynb** (Coming soon)
- Analyzing real-time data from Kafka
- Stream processing with AI
- Real-time predictions

### 3. **03_Deep_Learning_Basics.ipynb** (Coming soon)
- Introduction to neural networks
- Using TensorFlow/Keras
- TensorBoard visualization

## 🌐 Access Your Tools:

- **Jupyter Lab**: http://localhost:8888 (token: `ai-learning-2024`)
- **MLflow**: http://localhost:5001 (experiment tracking)
- **TensorBoard**: http://localhost:6006 (neural network visualization)
- **Grafana**: http://localhost:3000 (monitoring dashboards)

## 🎯 Getting Started:

1. **Start your services**:
   ```bash
   docker-compose -f fullstack/all-in-one.yaml up -d jupyter mlflow tensorboard
   ```

2. **Open Jupyter Lab**:
   - Go to http://localhost:8888
   - Enter token: `ai-learning-2024`
   - Navigate to `work/shared/` folder

3. **Begin learning**:
   - Start with `01_AI_Getting_Started.ipynb`
   - Run cells step by step
   - Experiment with the code!

## 📊 Your AI Infrastructure:

You now have a complete AI learning and development environment:

### **Data Sources**:
- PostgreSQL, MySQL, MongoDB databases
- Kafka streaming data
- Elasticsearch for search and analytics

### **AI/ML Tools**:
- **Jupyter**: Interactive development environment
- **MLflow**: Experiment tracking and model management
- **TensorBoard**: Neural network visualization
- **scikit-learn**: Traditional machine learning
- **TensorFlow**: Deep learning framework

### **Monitoring & Observability**:
- **Prometheus**: Metrics collection
- **Grafana**: Visualization dashboards
- **Loki**: Log aggregation
- **Jaeger**: Distributed tracing

## 🚀 Next Steps:

1. **Learn the basics** with the provided notebooks
2. **Experiment** with different algorithms and datasets
3. **Connect to your data** (Kafka, databases)
4. **Monitor your models** with your observability stack
5. **Deploy models** for real-time predictions

Happy learning! 🎉

## 🆘 Need Help?

- Check the notebook comments and markdown cells
- Visit MLflow UI for experiment details
- Use Grafana to monitor your AI services
- Explore the Jupyter documentation and tutorials online

Remember: AI is learned by doing - so start experimenting! 🧠✨
