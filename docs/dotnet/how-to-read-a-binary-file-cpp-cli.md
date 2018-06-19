---
title: 'Comment : lire un fichier binaire (C + c++ / CLI) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- files [C++], binary
- binary files, reading in C++
ms.assetid: 41ad9ad1-5cac-489c-874e-4bb3a649073a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8411971c8bca79d9cb1809481b5a6be61b052262
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33129367"
---
# <a name="how-to-read-a-binary-file-ccli"></a>Comment : lire un fichier binaire (C++/CLI)
L’exemple de code suivant montre comment lire des données binaires à partir d’un fichier, à l’aide de deux classes à partir de la <xref:System.IO?displayProperty=fullName> espace de noms : <xref:System.IO.FileStream> et <xref:System.IO.BinaryReader>. <xref:System.IO.FileStream> représente le fichier réel. <xref:System.IO.BinaryReader> Fournit une interface pour le flux de données qui autorise l’accès binaire.  
  
 L’exemple de code lit un fichier qui a appelé data.bin et contient des entiers au format binaire. Pour plus d’informations sur ce type de fichier, consultez [Comment : écrire un fichier binaire (C + c++ / CLI)](../dotnet/how-to-write-a-binary-file-cpp-cli.md).  
  
## <a name="example"></a>Exemple  
  
```  
// binary_read.cpp  
// compile with: /clr  
#using<system.dll>  
using namespace System;  
using namespace System::IO;  
  
int main()   
{  
   String^ fileName = "data.bin";  
   try  
   {  
      FileStream^ fs = gcnew FileStream(fileName, FileMode::Open);  
      BinaryReader^ br = gcnew BinaryReader(fs);  
  
      Console::WriteLine("contents of {0}:", fileName);  
      while (br->BaseStream->Position < br->BaseStream->Length)  
         Console::WriteLine(br->ReadInt32().ToString());  
  
      fs->Close( );  
   }  
   catch (Exception^ e)  
   {  
      if (dynamic_cast<FileNotFoundException^>(e))  
         Console::WriteLine("File '{0}' not found", fileName);  
      else  
         Console::WriteLine("Exception: ({0})", e);  
      return -1;  
   }  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fichier et flux de données E/S](http://msdn.microsoft.com/Library/4f4a33a9-66b7-4cd7-a285-4ad3e4276cd2)   
 [Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)