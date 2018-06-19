---
title: 'Comment : utiliser des Expressions régulières pour rechercher et remplacer (C + c++ / CLI) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- search and replace
- Replace method
- regular expressions [C++], search and replace
ms.assetid: 12fe3e18-fe10-4b25-a221-19dc5eab3821
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: feb64670accef1cdcc5eedf9aa2b081dc41615b6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33132412"
---
# <a name="how-to-use-regular-expressions-to-search-and-replace-ccli"></a>Comment : utiliser des expressions régulières pour les recherches et remplacements (C++/CLI)
L’exemple de code suivant montre comment la classe d’expression régulière <xref:System.Text.RegularExpressions.Regex> peut être utilisé pour effectuer la recherche et remplacement. Cette opération s’effectue avec la <xref:System.Text.RegularExpressions.Regex.Replace%2A> (méthode). La version utilisée prend deux chaînes comme entrée : la chaîne à modifier et la chaîne à insérer à la place les sections (le cas échéant) qui correspond au modèle donné à la <xref:System.Text.RegularExpressions.Regex> objet.  
  
 Ce code remplace tous les chiffres dans une chaîne avec des traits de soulignement (_), puis remplace les avec une chaîne vide, en les supprimant réellement. Le même effet peut être effectué en une seule étape, mais deux étapes sont utilisées ici à titre de démonstration.  
  
## <a name="example"></a>Exemple  
  
```  
// regex_replace.cpp  
// compile with: /clr  
#using <System.dll>  
using namespace System::Text::RegularExpressions;  
using namespace System;  
  
int main()  
{  
   String^ before = "The q43uick bro254wn f0ox ju4mped";  
   Console::WriteLine("original  : {0}", before);  
  
   Regex^ digitRegex = gcnew Regex("(?<digit>[0-9])");  
   String^ after = digitRegex->Replace(before, "_");  
   Console::WriteLine("1st regex : {0}", after);  
  
   Regex^ underbarRegex = gcnew Regex("_");  
   String^ after2 = underbarRegex->Replace(after, "");  
   Console::WriteLine("2nd regex : {0}", after2);  
  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [.NET Framework (expressions régulières)](/dotnet/standard/base-types/regular-expressions)   
 [Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)