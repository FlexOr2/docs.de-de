---
title: 'Vorgehensweise: Codieren und Decodieren ein JPEG-Bilds'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- encoding image formats [WPF]
- decoding JPEG images [WPF]
- encoding JPEG images [WPF]
- decoding image formats [WPF]
- JPEG decoding [WPF]
- JPEG encoding [WPF]
ms.assetid: b8cfde37-9f68-4911-a05e-51d8d7bdec7b
ms.openlocfilehash: 916eab63938100daf91e6c1a5af31648a99108d0
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027966"
---
# <a name="how-to-encode-and-decode-a-jpeg-image"></a>Vorgehensweise: Codieren und Decodieren ein JPEG-Bilds

Die folgenden Beispiele zeigen, wie Sie decodieren und Codieren eines JPEG-Bilds, indem der spezifische <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> und <xref:System.Windows.Media.Imaging.JpegBitmapEncoder> Objekte.  
  
## <a name="example---decode-a-jpeg-image"></a>Beispiel: Decodieren eines JPEG-Bilds

In diesem Beispiel wird veranschaulicht, wie eine JPEG-Bild mit decodieren eine <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> aus einem <xref:System.IO.FileStream>.  
  
[!code-cpp[JpegBitmapDecoderEncoder#1](~/samples/snippets/cpp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CPP/jpegencoderdecoder.cpp#1)]
[!code-csharp[JpegBitmapDecoderEncoder#1](~/samples/snippets/csharp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CSharp/JpegEncoderDecoder.cs#1)]
[!code-vb[JpegBitmapDecoderEncoder#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/VB/JpegEncoderDecoder.vb#1)]  
  
## <a name="example---encode-a-jpeg-image"></a>Beispiel: Codieren ein JPEG-Bilds

In diesem Beispiel wird veranschaulicht, wie zum Codieren einer <xref:System.Windows.Media.Imaging.BitmapSource> in das JPEG-Format image mit einer <xref:System.Windows.Media.Imaging.JpegBitmapEncoder>.  
  
[!code-cpp[JpegBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CPP/jpegencoderdecoder.cpp#4)]
[!code-csharp[JpegBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CSharp/JpegEncoderDecoder.cs#4)]
[!code-vb[JpegBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/VB/JpegEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a>Siehe auch

[Übersicht über die Bildverarbeitung](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)