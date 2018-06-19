---
title: 'Comment : écrire un fichier texte (C + c++ / CLI) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- files [C++], text
- text files, writing in C++
ms.assetid: 39ecdba6-84e0-485c-a202-84cf6d7b8d4a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7e0ce3839a5d0a0668d921a2d64cb0cf7bd1c775
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33131239"
---
# <a name="how-to-write-a-text-file-ccli"></a>Comment : écrire un fichier texte (C++/CLI)
L’exemple de code suivant montre comment créer un fichier texte et écrire du texte à l’aide de la <xref:System.IO.StreamWriter> (classe), qui est définie dans le <xref:System.IO> espace de noms. Le <xref:System.IO.StreamWriter> constructeur prend le nom du fichier à créer. Si le fichier existe, il est remplacé (à moins que vous transmettez la valeur True comme deuxième <xref:System.IO.StringWriter> argument du constructeur).  
  
 Le fichier est classé à l’aide de la <xref:System.IO.StreamWriter.Write%2A> et <xref:System.IO.TextWriter.WriteLine%2A> fonctions.  
  
## <a name="example"></a>Exemple  
  
```  
// text_write.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::IO;  
  
int main()   
{  
   String^ fileName = "textfile.txt";  
  
   StreamWriter^ sw = gcnew StreamWriter(fileName);  
   sw->WriteLine("A text file is born!");  
   sw->Write("You can use WriteLine");  
   sw->WriteLine("...or just Write");  
   sw->WriteLine("and do {0} output too.", "formatted");  
   sw->WriteLine("You can also send non-text objects:");  
   sw->WriteLine(DateTime::Now);  
   sw->Close();  
   Console::WriteLine("a new file ('{0}') has been written", fileName);  
  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fichier et flux de données E/S](http://msdn.microsoft.com/Library/4f4a33a9-66b7-4cd7-a285-4ad3e4276cd2)   
 [Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)