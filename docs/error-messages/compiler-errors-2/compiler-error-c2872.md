---
title: Erreur du compilateur C2872 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2872
dev_langs:
- C++
helpviewer_keywords:
- C2872
ms.assetid: c619ef97-6e0e-41d7-867c-f8d28a07d553
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 636f263382c41806e04c50c0770340305a3013ce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33247150"
---
# <a name="compiler-error-c2872"></a>Erreur du compilateur C2872
'*symbole*' : symbole ambigu  
  
Le compilateur ne peut pas déterminer le symbole que vous faites référence. Plusieurs symboles avec le nom spécifié est dans la portée. Consultez les remarques qui suivent le message d’erreur pour les emplacements de fichiers et les déclarations le compilateur a trouvé pour le symbole ambigu. Pour résoudre ce problème, vous pouvez qualifier entièrement le symbole ambigu à l’aide de son espace de noms, par exemple, `std::byte` ou `::byte`. Vous pouvez également utiliser un [alias d’espace de noms](../../cpp/namespaces-cpp.md#namespace_aliases) pour permettre à un espace de noms inclus un nom court pratique à utiliser lors de la lever les ambiguïtés entre les symboles dans votre code source.  
  
C2872 peut se produire si un fichier d’en-tête inclut un [à l’aide de la directive](../../cpp/namespaces-cpp.md#using_directives), et un fichier d’en-tête suivant est inclus qui contient un type qui est également dans l’espace de noms spécifié dans la `using` directive. Spécifiez un `using` directive uniquement après que tous les fichiers d’en-tête sont spécifiées avec `#include`.  
  
 Pour plus d’informations sur C2872, consultez les articles de la Base de connaissances [PRB : du compilateur erreurs lorsque vous utilisez #import avec XML dans Visual C++ .NET](http://support.microsoft.com/kb/316317) et [« erreur C2872 : 'Plateforme' : symbole ambigu « message d’erreur lorsque vous utilisez le Espace de noms Windows::Foundation::Metadata dans Visual Studio 2013](https://support.microsoft.com/kb/2890859).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C2872, car une référence ambiguë est effectuée pour une variable nommée `i`; deux variables portant le même nom se trouvent dans la portée :  
  
```cpp  
// C2872.cpp  
// compile with: cl /EHsc C2872.cpp  
namespace A {  
   int i;  
}  
  
using namespace A;  
int i;  
int main() {  
   ::i++;   // ok, uses i from global namespace  
   A::i++;   // ok, uses i from namespace A  
   i++;   // C2872 ambiguous: ::i or A::i? 
   // To fix this issue, use the fully qualified name
   // for the intended variable. 
}  
```