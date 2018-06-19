---
title: 'Comment : réorganiser des données à l’aide d’Expressions régulières (C + c++ / CLI) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- regular expressions [C++], rearranging data
- data [C++], rearranging
ms.assetid: 5f91e777-9471-424e-ba75-dca3d1b49e42
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 72c72721aa68417ff13905fdf96f8d2a48b310cd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33130862"
---
# <a name="how-to-use-regular-expressions-to-rearrange-data-ccli"></a>Comment : réorganiser des données à l'aide d'expressions régulières (C++/CLI)
L’exemple de code suivant montre comment la prise en charge des expressions régulières .NET Framework peut être utilisé pour réorganiser ou reformater les données. Le code suivant exemple utilise le <xref:System.Text.RegularExpressions.Regex> et <xref:System.Text.RegularExpressions.Match> classes pour extraire les prénoms et les noms d’une chaîne et afficher ces éléments dans l’ordre inverse.  
  
 La <xref:System.Text.RegularExpressions.Regex> classe est utilisée pour construire une expression régulière qui décrit le format actuel des données. Les deux noms sont supposés être séparés par une virgule et peuvent utiliser un nombre quelconque d’espaces blancs autour de la virgule. Le <xref:System.Text.RegularExpressions.Match> méthode est ensuite utilisée pour analyser chaque chaîne. En cas de réussite, les prénoms et les noms sont récupérés à partir de la <xref:System.Text.RegularExpressions.Match> de l’objet et l’affiche.  
  
## <a name="example"></a>Exemple  
  
```  
// regex_reorder.cpp  
// compile with: /clr  
#using <System.dll>  
using namespace System;  
using namespace Text::RegularExpressions;  
  
int main()  
{  
   array<String^>^ name =   
   {  
      "Abolrous, Sam",   
      "Berg,Matt",   
      "Berry , Jo",  
      "www.contoso.com"  
   };  
  
   Regex^ reg = gcnew Regex("(?<last>\\w*)\\s*,\\s*(?<first>\\w*)");  
  
   for ( int i=0; i < name->Length; i++ )  
   {  
      Console::Write( "{0,-20}", name[i] );  
      Match^ m = reg->Match( name[i] );  
      if ( m->Success )  
      {  
         String^ first = m->Groups["first"]->Value;  
         String^ last = m->Groups["last"]->Value;  
         Console::WriteLine("{0} {1}", first, last);  
      }  
      else  
         Console::WriteLine("(invalid)");  
   }  
   return 0;  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [.NET Framework (expressions régulières)](/dotnet/standard/base-types/regular-expressions)   
 [Programmation .NET avec C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)