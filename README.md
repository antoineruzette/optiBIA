[![License](https://img.shields.io/pypi/l/microsim.svg?color=green)](https://github.com/antoineruzette/auto-bia-workflow/blob/main/LICENSE)
[![PyPI](https://img.shields.io/pypi/v/auto-bia-workflow.svg?color=green)](https://pypi.org/project/auto-bia-workflow/)
[![Python Version](https://img.shields.io/pypi/pyversions/auto-bia-workflow.svg?color=green)](https://python.org)
[![Downloads](https://pepy.tech/badge/auto-bia-workflow)](https://pepy.tech/project/auto-bia-workflow)
[![Build Status](https://travis-ci.com/antoineruzette/auto-bia-workflow.svg?branch=main)](https://travis-ci.com/antoineruzette/auto-bia-workflow)
[![Coverage Status](https://coveralls.io/repos/github/antoineruzette/auto-bia-workflow/badge.svg?branch=main)](https://coveralls.io/github/antoineruzette/auto-bia-workflow?branch=main

# AutoBIA

AutoBIA is a Python library to optimize image analysis workflows. It allows users to create and apply various image processing operators in a sequential manner, and optimize the parameters of these operators to achieve the best results. 

## Installation

1. **Clone the repository**: Clone this repository to your local machine using Git.
The library is not stable at this point and new features are added regularly. For now, the best way to install the library is to clone the repository and locally install the package using pip.

    ```bash
    git clone https://github.com/antoineruzette/auto-bia-workflow.git
    ```
2. **Install the dependencies**: Install the dependencies using pip.

    ```bash
    pip install -r requirements.txt
    ```
3. **Install the package**: Install the package using pip.

    ```bash
    pip install dist/auto_bia-0.1-py3-none-any.whl
    ```

## Usage
Construct a workflow by adding operators and setting their initial parameters, then optimize workflow using the `optimize` method. The `optimize` method uses a gradient descent algorithm to find the best parameters for the operators in the workflow.

```python

from auto_bia import bia_workflow as biaw

# Create an image analysis workflow
workflow = biaw.ImageAnalysisWorkflow()
# Add operators to the workflow
workflow.add_operator(biaw.SmoothingOperator(kernel_size=5))
workflow.add_operator(biaw.SegmentationOperator(threshold=30))
# Set optimization parameters
workflow.set_cutoff(0.95)

# Run it
image_path = "/tests/images/original.png"
mask_path = "/tests/images/mask.png"
result_save_path = "/tests/images/result.png"
workflow.run(image_path, mask_path, result_save_path)
```
