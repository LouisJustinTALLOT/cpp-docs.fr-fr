---
title: Opérations graphiques (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- GDI+ [C++]
- .NET Framework [C++], graphics
- images [C++], .NET Framework and
- GDI+ [C++], about graphics operations
- graphics [C++], .NET Framework and
- GDI+ [C++], displaying images
- graphics [C++], displaying images
- GDI+, drawing shapes
- drawing, shapes
- shapes
- shapes, drawing
- GDI+ [C++], rotating images
- graphics [C++], rotating images
- GDI+ [C++], converting image file formats
- graphics [C++], converting image file formats
ms.assetid: bba27228-b9b3-4c9c-b31c-a04b76702a95
ms.openlocfilehash: c7c6d62eb4059069e6e266544ce6323c63dd15c0
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57746277"
---
# <a name="graphics-operations-ccli"></a>Opérations graphiques (C++/CLI)

Illustre la manipulation d’image à l’aide du Kit de développement logiciel Windows.

Les rubriques suivantes illustrent l’utilisation de la <xref:System.Drawing.Image?displayProperty=fullName> classe pour effectuer une manipulation d’image.

## <a name="display"></a> Afficher des Images avec le .NET Framework

L’exemple de code suivant modifie le Gestionnaire d’événements OnPaint pour récupérer un pointeur vers le <xref:System.Drawing.Graphics> objet pour le formulaire principal. Le <xref:System.Windows.Forms.Form.OnPaint%2A> (fonction) est destinée à une application Windows Forms, très probablement créée avec l’Assistant application Visual Studio.

L’image est représentée par la <xref:System.Drawing.Image> classe. Les données d’image sont chargées à partir d’un fichier .jpg à l’aide du <xref:System.Drawing.Image.FromFile%2A?displayProperty=fullName> (méthode). Avant que l’image est dessinée au formulaire, le formulaire est redimensionné pour s’adapter à l’image. Le dessin de l’image est effectué avec la <xref:System.Drawing.Graphics.DrawImage%2A?displayProperty=fullName> (méthode).

Le <xref:System.Drawing.Graphics> et <xref:System.Drawing.Image> classes sont toutes deux dans le <xref:System.Drawing?displayProperty=fullName> espace de noms.

### <a name="example"></a>Exemple

```cpp
#using <system.drawing.dll>

using namespace System;
using namespace System::Drawing;

protected:
virtual Void Form1::OnPaint(PaintEventArgs^ pe) override
{
    Graphics^ g = pe->Graphics;
    Image^ image = Image::FromFile("SampleImage.jpg");
    Form::ClientSize = image->Size;
    g->DrawImage( image, 0, 0, image->Size.Width, image->Size.Height );
}
```

## <a name="draw"></a> Dessiner des formes avec le .NET Framework

Le code suivant exemple utilise le <xref:System.Drawing.Graphics> classe pour modifier le <xref:System.Windows.Forms.Form.OnPaint%2A> Gestionnaire d’événements pour récupérer un pointeur vers le <xref:System.Drawing.Graphics> objet pour le formulaire principal. Ce pointeur est ensuite utilisé pour définir la couleur d’arrière-plan du formulaire et dessiner une ligne et un à l’aide de l’arc le <xref:System.Drawing.Graphics.DrawLine%2A?displayProperty=fullName> et <xref:System.Drawing.Graphics.DrawArc%2A> méthodes.

### <a name="example"></a>Exemple

```cpp
#using <system.drawing.dll>
using namespace System;
using namespace System::Drawing;
// ...
protected:
virtual Void Form1::OnPaint(PaintEventArgs^ pe ) override
{
   Graphics^ g = pe->Graphics;
   g->Clear(Color::AntiqueWhite);

   Rectangle rect = Form::ClientRectangle;
   Rectangle smallRect;
   smallRect.X = rect.X + rect.Width / 4;
   smallRect.Y = rect.Y + rect.Height / 4;
   smallRect.Width = rect.Width / 2;
   smallRect.Height = rect.Height / 2;

   Pen^ redPen = gcnew Pen(Color::Red);
   redPen->Width = 4;
   g->DrawLine(redPen, 0, 0, rect.Width, rect.Height);

   Pen^ bluePen = gcnew Pen(Color::Blue);
   bluePen->Width = 10;
   g->DrawArc( bluePen, smallRect, 90, 270 );
}
```

## <a name="rotate"></a> Faire pivoter des Images avec le .NET Framework

L’exemple de code suivant illustre l’utilisation de la <xref:System.Drawing.Image?displayProperty=fullName> classe pour charger une image à partir du disque, faire pivoter de 90 degrés et enregistrez-le en tant que nouveau fichier .jpg.

### <a name="example"></a>Exemple

```cpp
#using <system.drawing.dll>

using namespace System;
using namespace System::Drawing;

int main()
{
   Image^ image = Image::FromFile("SampleImage.jpg");
   image->RotateFlip( RotateFlipType::Rotate90FlipNone );
   image->Save("SampleImage_rotated.jpg");
   return 0;
}
```

## <a name="convert"></a> Convertir des Formats de fichiers d’Image avec le .NET Framework

L’exemple de code suivant montre le <xref:System.Drawing.Image?displayProperty=fullName> classe et le <xref:System.Drawing.Imaging.ImageFormat?displayProperty=fullName> énumération utilisée pour convertir et enregistrer des fichiers image. Le code suivant charge une image à partir d’un fichier .jpg et puis l’enregistre dans les formats de fichier .gif et .bmp.

### <a name="example"></a>Exemple

```cpp
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

## <a name="related-sections"></a>Rubriques connexes

[Mise en route de la programmation graphique](/dotnet/framework/winforms/advanced/getting-started-with-graphics-programming)

[À propos du code managé GDI+](/dotnet/framework/winforms/advanced/about-gdi-managed-code)

## <a name="see-also"></a>Voir aussi

[Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

<xref:System.Drawing>
