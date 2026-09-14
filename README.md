# Artificial Neural Networks

A hands-on introduction to artificial neural networks with TensorFlow and Keras. Over three days of exercises you progress from dense networks to convolutional networks and transfer learning, with an optional bonus that builds a network from scratch.

## Learning Objectives

By the end of this repository, you should be able to:

- Build and train dense neural networks for regression and classification with TensorFlow and Keras.
- Diagnose over- and underfitting and apply regularisation, dropout, and early stopping to address it.
- Save and reload trained Keras models for reuse.
- Implement a convolutional neural network for image classification.
- Apply transfer learning to adapt a pretrained network to a new task.
- Implement a dense network and its back-propagation from scratch with NumPy.

## Learning Path

The notebooks are grouped by day and build on each other in order:


### Day 1 - Dense Neural Networks

Implement dense neural networks for regression and classification. The course uses TensorFlow and Keras throughout.

| File | Description |
|---|---|
| [**01 - Regression with TensorFlow and Keras**](day_1/01_regression_tensorflow_keras.ipynb) | Build a dense network to predict a continuous target. |
| [**02 - Classification with TensorFlow and Keras**](day_1/02_classification_tensorflow_keras.ipynb) | Build a dense network for a classification problem. |

### Day 2 - Regularisation and Model Persistence

Diagnose over- and underfitting, then save and reload trained models.

| File | Description |
|---|---|
| [**03 - Over- and Underfitting**](day_2/03_overfit_underfit.ipynb) | Compare model capacities and apply regularisation and dropout. |
| [**04 - Save and Load Models**](day_2/04_load_saved_models.ipynb) | Persist and reload a trained Keras model (optional). |

### Day 3 - Convolutions and Transfer Learning

Move from dense to convolutional networks, then reuse a pretrained network on a new task.

| File | Description |
|---|---|
| [**05 - CNN with Keras**](day_3/cnn/cnn_keras.ipynb) | Build a convolutional neural network for image classification. |
| [**06 - Pretrained Networks and Transfer Learning**](day_3/pretrained_transfer_learning/pretrained_networks-transfer_learning.ipynb) | Adapt a pretrained VGG16 network to classify new images. |

### Bonus

Optional deep-dive once you finish the other days. You rarely build a network from scratch in practice, but doing it once makes training far easier to understand.

| File | Description |
|---|---|
| [**00 - DNN from Scratch**](bonus/00_dnn_from_scratch.ipynb) | Implement a dense network and its back-propagation with NumPy. |

### Additional Folders and Files

| File / Folder | Description |
|---|---|
| [**Solutions**](solutions/) | Reference solutions. |
| [**pyproject.toml**](pyproject.toml) | Project configuration and dependencies. |
| [**uv.lock**](uv.lock) | Dependency lock file. |

## Setup

> [!NOTE]
> Throughout these steps, text in angle brackets like `<repo-name>` is a **placeholder**. Replace it, including the `< >` brackets, with your own value. For example, `cd <repo-name>` becomes `cd my-ann-project`.

### 1. Create the Repository from the Template

Click **Use this template** on GitHub.

When creating the repository:

- Set yourself as the **Owner**
- Choose a repository name
- Disable **Include all branches**
- Click **Create repository**

> [!IMPORTANT]
> If you are working in pairs or groups, only **one person** should complete this step.

---

### 2. Add Collaborators (Pairs/Groups Only)

If working with teammates:

1. Open the repository on GitHub
2. Go to **Settings → Collaborators**
3. Add your teammates as collaborators
4. Share the repository link with your team

Teammates should accept the invitation before continuing.

---

### 3. Clone the Repository

Copy the SSH URL from the **Code** button on GitHub, then run:

```bash
git clone <copied-ssh-url>
```

The copied SSH URL will look like `git@github.com:<your-username>/<repo-name>.git`.

---

### 4. Move into the Project Folder and Install Dependencies

This installs all dependencies and creates a virtual environment in (`.venv/`).

```bash
cd <repo-name>
uv sync
```

---

### 5. Unzip the Data

The datasets are bundled as zip archives that extract into git-ignored `data/` folders. There are two, in different locations. These commands use the environment from `uv sync`:

The tabular datasets used in the Day 1 and Day 2 notebooks (`boston.csv`, `titanic.csv`, `vehicle_emissions.csv`):

```bash
uv run python -c "import zipfile; zipfile.ZipFile('data.zip').extractall()"
```

The image dataset used by the transfer-learning notebook:

```bash
uv run python -c "import zipfile; zipfile.ZipFile('day_3/pretrained_transfer_learning/data.zip').extractall('day_3/pretrained_transfer_learning')"
```

---

### 6. Open the Notebooks

> [!NOTE]
> Make sure you open VS Code from the project root so it automatically detects the environment created by `uv sync`.

Launch VS Code in the project root folder:

```bash
code .
```

Then open a notebook and select the Python environment created by `uv sync` as the kernel.

## References & Further Reading

- [**Keras: The high-level API for TensorFlow**](https://www.tensorflow.org/guide/keras): Official guide to building models with Keras.
- [**Overfit and Underfit**](https://www.tensorflow.org/tutorials/keras/overfit_and_underfit): TensorFlow tutorial on diagnosing and controlling model fit.
- [**Transfer Learning and Fine-tuning**](https://keras.io/guides/transfer_learning/): Keras guide to reusing pretrained networks.
- [**Get Started with TensorBoard**](https://www.tensorflow.org/tensorboard/get_started): Visualise training metrics and model graphs.
- [**A Neural Network Playground**](https://playground.tensorflow.org/): Tinker with a small neural network in your browser to build intuition.
