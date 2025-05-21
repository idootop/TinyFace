# TinyFace

<a href="https://pypi.python.org/pypi/tinyface"><img src="http://img.shields.io/pypi/v/tinyface.svg" alt="Latest version on PyPI"></a> <a href="https://pypi.python.org/pypi/tinyface"><img src="http://img.shields.io/pypi/dm/tinyface.svg" alt="Monthly downloads on PyPI"></a> <a href="https://pypi.python.org/pypi/tinyface"><img src="https://img.shields.io/pypi/pyversions/tinyface.svg" alt="Compatible Python versions."></a>

TinyFace is designed as a lightweight Python library with a simplified command-line interface, making it easy for both developers and users to perform face swaps.

## Features

- **Minimalist design**: Focuses solely on face swapping with optimized speed and minimal dependencies.
- **Easy-to-use API**: Integrate face swapping into your own projects with just a few lines of code.
- **Single and multi-face support**: Swap a single face or multiple faces in one go.
- **Command-line tool**: Easily perform face swaps directly from the terminal.

## Installation

Install `tinyface` with pip:

```bash
pip install tinyface
```

## Usage

```python
import cv2

from tinyface import FacePair, TinyFace

# Load input images
input_img = cv2.imread("input.jpg")
reference_img = cv2.imread("reference.jpg")
destination_img = cv2.imread("destination.jpg")

# Initialize the TinyFace instance
tinyface = TinyFace()

# (Optional) Prepare models (downloads automatically if skipped)
tinyface.prepare()

# Detect faces in the images
faces = tinyface.get_many_faces(input_img)
reference_face = tinyface.get_one_face(reference_img)
destination_face = tinyface.get_one_face(destination_img)

# Swap a single face
output_img = tinyface.swap_face(input_img, reference_face, destination_face)

# Swap multiple faces
output_img = tinyface.swap_faces(
    input_img,
    face_pairs=[FacePair(reference=reference_face, destination=destination_face)],
)
cv2.imwrite("out.jpg", output_img)
```

## Commands

```bash
usage: tinyface swap [-h] -i INPUT -r REFERENCE -d DESTINATION [-s SAVE] [-w WORKERS]

options:
  -h, --help            Show this help message and exit
  -i INPUT, --input INPUT
                        Path to the input image(s)
  -r REFERENCE, --reference REFERENCE
                        Path to the reference face image(s)
  -d DESTINATION, --destination DESTINATION
                        Path to the destination face image(s)
  -s SAVE, --save SAVE  Save path for output image(s)
  -w WORKERS, --workers WORKERS
                        Number of worker threads for parallel processing
```

## Projects using TinyFace

- [MagicMirror](https://github.com/idootop/MagicMirror): Instant AI Face Swap — One click to a brand new you! 一键 AI 换脸，发现更美的自己 ✨

## Disclaimer

This software is intended to contribute positively to the AI-generated media field, helping artists with tasks like character animation and clothing model creation.

Please use responsibly. If working with real faces, always obtain consent and label deepfakes clearly when sharing. The developers are not responsible for any misuse or legal consequences.

## Credits

This project is built upon [@henryruhs](https://github.com/henryruhs)'s work on [facefusion](https://github.com/facefusion/facefusion). TinyFace retains only the minimal dependencies required for face swapping, optimizing both speed and size.

## License

This project is licensed under the MIT License - see the [LICENSE](./LICENSE) file for details.

> **Note:** TinyFace relies on third-party pre-trained models, each with their own licenses and terms.
