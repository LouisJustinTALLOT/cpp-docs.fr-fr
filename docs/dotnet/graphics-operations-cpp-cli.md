---
description: 'En savoir plus sur : opérations graphiques (C++/CLI)'
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
ms.openlocfilehash: 84dbc75aa306219b8733848ece5c594ca40a0489
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97223540"
---
# <a name="graphics-operations-ccli"></a>Opérations graphiques (C++/CLI)

Illustre la manipulation d’images à l’aide de l’SDK Windows.

Les rubriques suivantes illustrent l’utilisation de la <xref:System.Drawing.Image?displayProperty=fullName> classe pour effectuer une manipulation d’image.

## <a name="display-images-with-the-net-framework"></a><a name="display"></a> Afficher les images avec le .NET Framework

L’exemple de code suivant modifie le gestionnaire d’événements OnPaint pour récupérer un pointeur vers l' <xref:System.Drawing.Graphics> objet pour le formulaire principal. La <xref:System.Windows.Forms.Form.OnPaint%2A> fonction est destinée à une application Windows Forms, probablement créée à l’aide d’un Assistant application Visual Studio.

L’image est représentée par la <xref:System.Drawing.Image> classe. Les données de l’image sont chargées à partir d’un fichier. jpg à l’aide de la <xref:System.Drawing.Image.FromFile%2A?displayProperty=fullName> méthode. Avant que l’image ne soit dessinée dans le formulaire, le formulaire est redimensionné pour s’adapter à l’image. Le dessin de l’image est effectué à l’aide de la <xref:System.Drawing.Graphics.DrawImage%2A?displayProperty=fullName> méthode.

Les <xref:System.Drawing.Graphics> <xref:System.Drawing.Image> classes et sont toutes deux dans l' <xref:System.Drawing?displayProperty=fullName> espace de noms.

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

## <a name="draw-shapes-with-the-net-framework"></a><a name="draw"></a> Dessiner des formes avec le .NET Framework

L’exemple de code suivant utilise la <xref:System.Drawing.Graphics> classe pour modifier le <xref:System.Windows.Forms.Form.OnPaint%2A> Gestionnaire d’événements afin de récupérer un pointeur vers l' <xref:System.Drawing.Graphics> objet pour le formulaire principal. Ce pointeur est ensuite utilisé pour définir la couleur d’arrière-plan du formulaire et dessiner une ligne et un arc à l’aide des <xref:System.Drawing.Graphics.DrawLine%2A?displayProperty=fullName> <xref:System.Drawing.Graphics.DrawArc%2A> méthodes et.

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

## <a name="rotate-images-with-the-net-framework"></a><a name="rotate"></a> Faire pivoter des images avec le .NET Framework

L’exemple de code suivant illustre l’utilisation de la <xref:System.Drawing.Image?displayProperty=fullName> classe pour charger une image à partir du disque, la faire pivoter de 90 degrés et l’enregistrer dans un nouveau fichier. jpg.

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

## <a name="convert-image-file-formats-with-the-net-framework"></a><a name="convert"></a> Convertir les formats de fichier image avec le .NET Framework

L’exemple de code suivant illustre la <xref:System.Drawing.Image?displayProperty=fullName> classe et l' <xref:System.Drawing.Imaging.ImageFormat?displayProperty=fullName> énumération utilisées pour convertir et enregistrer des fichiers image. Le code suivant charge une image à partir d’un fichier. jpg, puis l’enregistre dans les formats de fichier. gif et. bmp.

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

## <a name="related-sections"></a>Sections connexes

[Mise en route de la programmation graphique](/dotnet/framework/winforms/advanced/getting-started-with-graphics-programming)

[À propos du code managé GDI+](/dotnet/framework/winforms/advanced/about-gdi-managed-code)

## <a name="see-also"></a>Voir aussi

[Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

<xref:System.Drawing>
