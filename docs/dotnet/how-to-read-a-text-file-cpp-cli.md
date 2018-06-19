---
title: 'Comment : lire un fichier texte (C + c++ / CLI) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- reading text files
- text files, reading
ms.assetid: 80551c01-d769-4b6d-8db7-fd53bde21b62
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: c350ea9cd8b71378d059a93ac80ca808d4f48790
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33130196"
---
# <a name="how-to-read-a-text-file-ccli"></a>Comment : lire un fichier texte (C++/CLI)
L’exemple de code suivant montre comment ouvrir et lire une fichier texte une ligne à la fois, à l’aide de la <xref:System.IO.StreamReader> classe qui est définie dans le <xref:System.IO?displayProperty=fullName> espace de noms. Une instance de cette classe est utilisée pour ouvrir un fichier texte, puis la <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=fullName> méthode est utilisée pour récupérer chaque ligne.  
  
 Cet exemple de code lit un fichier a nommé textfile.txt et contienne du texte. Pour plus d’informations sur ce type de fichier, consultez [Comment : écrire un fichier texte (C + c++ / CLI)](../dotnet/how-to-write-a-text-file-cpp-cli.md).  
  
## <a name="example"></a>Exemple  
  
```  
// text_read.cpp  
// compile with: /clr  
#using<system.dll>  
using namespace System;  
using namespace System::IO;  
  
int main()  
{  
   String^ fileName = "textfile.txt";  
   try   
   {  
      Console::WriteLine("trying to open file {0}...", fileName);  
      StreamReader^ din = File::OpenText(fileName);  
  
      String^ str;  
      int count = 0;  
      while ((str = din->ReadLine()) != nullptr)   
      {  
         count++;  
         Console::WriteLine("line {0}: {1}", count, str );  
      }  
   }  
   catch (Exception^ e)  
   {  
      if (dynamic_cast<FileNotFoundException^>(e))  
         Console::WriteLine("file '{0}' not found", fileName);  
      else  
         Console::WriteLine("problem reading file '{0}'", fileName);  
   }  
  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fichier et flux de données E/S](http://msdn.microsoft.com/Library/4f4a33a9-66b7-4cd7-a285-4ad3e4276cd2)   
 [Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)