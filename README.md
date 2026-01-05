# multimodal-image-captioner-architecture
**🧠 Architecture (brief)**

Encoder: pretrained vision backbone (ResNet/timm/CLIP) → image features (pooled/flattened or spatial map)

Decoder: Transformer decoder that attends to image features via cross-attention, produces token-by-token captions with embedding & positional encodings

Loss: supervised cross-entropy with teacher-forcing; optional label smoothing.

💡 Approach

Built a reusable PyTorch pipeline with custom Dataset and DataLoader classes to load image–caption pairs.

Applied image preprocessing and augmentation (torchvision.transforms, PIL/OpenCV): resize, random crop/flip, normalization — to improve generalization.

Used a pretrained vision encoder (ResNet / timm model / CLIP visual backbone) as feature extractor.

Implemented a Transformer decoder that consumes encoded image features and generates captions token-by-token using an embedding layer and positional encodings.

Added cross-attention between image features and decoder tokens to ground generated words in visual features.

Trained with supervised cross-entropy loss and teacher-forcing; optionally used scheduled sampling to reduce exposure bias.

Implemented knowledge-aware regularization (label smoothing, weight decay) and applied gradient clipping to stabilize training.

✅ Impact

Achieved stable convergence with a final training loss of 0.337, demonstrating an effective multimodal image captioning system capable of generating semantically meaningful captions for real-world images, enabling vision-language applications.


