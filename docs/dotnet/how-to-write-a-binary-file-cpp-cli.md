---
title: 'Comment : écrire un fichier binaire (C + c++ / CLI) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- binary files, writing in C++
- files [C++], binary
ms.assetid: 35d97ee6-fc7e-4c36-be18-8bbb3b44b3ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 69467b913ea76b5f5e19772ee7d0d846a363c5e7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33130125"
---
# <a name="how-to-write-a-binary-file-ccli"></a>Comment : écrire un fichier binaire (C++/CLI)
L’exemple de code suivant montre comment écrire des données binaires dans un fichier. Deux classes à partir de la <xref:System.IO> espace de noms sont utilisés : <xref:System.IO.FileStream> et <xref:System.IO.BinaryWriter>. <xref:System.IO.FileStream> représente le fichier réel, tandis que <xref:System.IO.BinaryWriter> fournit une interface pour le flux de données qui autorise l’accès binaire.  
  
 L’exemple de code suivant écrit un fichier contenant des entiers au format binaire. Ce fichier peut être lu par le code de [Comment : lire un fichier binaire (C + c++ / CLI)](../dotnet/how-to-read-a-binary-file-cpp-cli.md).  
  
## <a name="example"></a>Exemple  
  
```  
// binary_write.cpp  
// compile with: /clr  
#using<system.dll>  
using namespace System;  
using namespace System::IO;  
  
int main()  
{  
   array<Int32>^ data = {1, 2, 3, 10000};  
  
   FileStream^ fs = gcnew FileStream("data.bin", FileMode::Create);  
   BinaryWriter^ w = gcnew BinaryWriter(fs);  
  
   try   
   {  
      Console::WriteLine("writing data to file:");  
      for (int i=0; i<data->Length; i++)  
      {  
         Console::WriteLine(data[i]);  
         w->Write(data[i]);  
      }  
   }  
   catch (Exception^)   
   {  
     Console::WriteLine("data could not be written");  
     fs->Close();  
     return -1;  
   }  
  
   fs->Close();  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fichier et flux de données E/S](http://msdn.microsoft.com/Library/4f4a33a9-66b7-4cd7-a285-4ad3e4276cd2)   
 [Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)