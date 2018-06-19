---
title: 'Comment : convertir des Formats de fichier d’Image avec le .NET Framework | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- GDI+ [C++], converting image file formats
- graphics [C++], converting image file formats
ms.assetid: 5d5384b0-b9b7-4262-b9ad-c4cb95f75ee4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 98d55c7ee4ca967a0b52bd87b22e5c316eb1e274
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33130056"
---
# <a name="how-to-convert-image-file-formats-with-the-net-framework"></a>Comment : convertir des fichiers au format image avec le .NET Framework
L’exemple de code suivant montre la <xref:System.Drawing.Image?displayProperty=fullName> classe et le <xref:System.Drawing.Imaging.ImageFormat?displayProperty=fullName> énumération utilisée pour convertir et enregistrer des fichiers image. Le code suivant charge une image à partir d’un fichier .jpg et puis l’enregistre dans des formats de fichier .gif et .bmp.  
  
## <a name="example"></a>Exemple  
  
```  
#using <system.drawing.dll>  
  
using namespace System;  
using namespace System::Drawing;  
using namespace System::Drawing::Imaging;  
  
int main()  
{  
   Image^ image = Image::FromFile("SampleImage.jpg");  
   image->Save("SampleImage.png", ImageFormat::Png);  
   image->Save("SampleImage.bmp", ImageFormat::Bmp);  
  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Drawing>   
 [Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)