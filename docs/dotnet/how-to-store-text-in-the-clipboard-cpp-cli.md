---
title: 'Comment : stocker du texte dans le Presse-papiers (C + c++ / CLI) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- text, storing in Clipboard
- Clipboard, storing text
ms.assetid: 9996023f-b700-47ad-8ad9-1ba201eaa5a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9ac33eb31dbda97d3c695847344cd857d2e77675
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33138517"
---
# <a name="how-to-store-text-in-the-clipboard-ccli"></a>Comment : stocker du texte dans le Presse-papiers (C++/CLI)
Le code suivant exemple utilise le <xref:System.Windows.Forms.Clipboard> objet défini dans le <xref:System.Windows.Forms> espace de noms pour stocker une chaîne. Cet objet fournit deux fonctions membres : <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> et <xref:System.Windows.Forms.Clipboard.GetDataObject%2A>. Données sont stockées dans le Presse-papiers en envoyant tout objet dérivé <xref:System.Object> à <xref:System.Windows.Forms.Clipboard.SetDataObject%2A>.  
  
## <a name="example"></a>Exemple  
  
```  
// store_clipboard.cpp  
// compile with: /clr  
#using <System.dll>  
#using <System.Drawing.dll>  
#using <System.Windows.Forms.dll>  
  
using namespace System;  
using namespace System::Windows::Forms;  
  
[STAThread] int main()  
{  
   String^ str = "This text is copied into the Clipboard.";  
  
   // Use 'true' as the second argument if  
   // the data is to remain in the clipboard  
   // after the program terminates.  
   Clipboard::SetDataObject(str, true);  
  
   Console::WriteLine("Added text to the Clipboard.");  
  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : récupérer du texte dans le Presse-papiers (C + c++ / CLI)](../dotnet/how-to-retrieve-text-from-the-clipboard-cpp-cli.md)   
 [Opérations Windows (C + c++ / CLI)](../dotnet/windows-operations-cpp-cli.md)   
 [Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)