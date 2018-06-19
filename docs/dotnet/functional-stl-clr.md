---
title: fonctionnel (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- <cliext/functional>
dev_langs:
- C++
helpviewer_keywords:
- <functional> header [STL/CLR]
- <cliext/functional> header [STL/CLR]
- functional functions [STL/CLR]
ms.assetid: 88738b8c-5d37-4375-970e-a4442bf5efde
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 38bfbe025c92aa54956a165367b367cecc6160b2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33112834"
---
# <a name="functional-stlclr"></a>functional (STL/CLR)
Incluez l’en-tête STL/CLR `<cliext/functional>` pour définir l’un nombre de classes de modèle et les fonctions et les délégués de modèle associés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#include <functional>  
```  
  
## <a name="declarations"></a>Déclarations  
  
|délégué|Description|  
|--------------|-----------------|  
|[binary_delegate (STL/CLR)](../dotnet/binary-delegate-stl-clr.md)|Délégué à deux arguments.|  
|[binary_delegate_noreturn (STL/CLR)](../dotnet/binary-delegate-noreturn-stl-clr.md)|Délégué à deux arguments retournant `void`.|  
|[unary_delegate (STL/CLR)](../dotnet/unary-delegate-stl-clr.md)|Délégué à un argument.|  
|[unary_delegate_noreturn (STL/CLR)](../dotnet/unary-delegate-noreturn-stl-clr.md)|Délégué à un argument retour `void`.|  
  
|Classe|Description|  
|-----------|-----------------|  
|[binary_negate (STL/CLR)](../dotnet/binary-negate-stl-clr.md)|Functor pour annuler un functor deux arguments.|  
|[binder1st (STL/CLR)](../dotnet/binder1st-stl-clr.md)|Functor pour lier le premier argument à un functor deux arguments.|  
|[binder2nd (STL/CLR)](../dotnet/binder2nd-stl-clr.md)|Functor pour lier le deuxième argument à un functor deux arguments.|  
|[divides (STL/CLR)](../dotnet/divides-stl-clr.md)|Diviser functor.|  
|[equal_to (STL/CLR)](../dotnet/equal-to-stl-clr.md)|Fonction de comparaison égale.|  
|[greater (STL/CLR)](../dotnet/greater-stl-clr.md)|Fonction de comparaison supérieure.|  
|[greater_equal (STL/CLR)](../dotnet/greater-equal-stl-clr.md)|Fonction de comparaison supérieur ou égal à.|  
|[less (STL/CLR)](../dotnet/less-stl-clr.md)|Moins functor de comparaison.|  
|[less_equal (STL/CLR)](../dotnet/less-equal-stl-clr.md)|Fonction de comparaison inférieur ou égal à.|  
|[logical_and (STL/CLR)](../dotnet/logical-and-stl-clr.md)|Logique AND functor.|  
|[logical_not (STL/CLR)](../dotnet/logical-not-stl-clr.md)|Logique pas functor.|  
|[logical_or (STL/CLR)](../dotnet/logical-or-stl-clr.md)|Functor de OR logique.|  
|[minus (STL/CLR)](../dotnet/minus-stl-clr.md)|Soustraire functor.|  
|[modulus (STL/CLR)](../dotnet/modulus-stl-clr.md)|Functor de modulo.|  
|[multiplies (STL/CLR)](../dotnet/multiplies-stl-clr.md)|Multipliez functor.|  
|[negate (STL/CLR)](../dotnet/negate-stl-clr.md)|Functor pour retourner l’argument de l’opération de négation.|  
|[not_equal_to (STL/CLR)](../dotnet/not-equal-to-stl-clr.md)|Fonction de comparaison n’est pas égal.|  
|[plus (STL/CLR)](../dotnet/plus-stl-clr.md)|Ajoutez un functor.|  
|[unary_negate (STL/CLR)](../dotnet/unary-negate-stl-clr.md)|Functor pour annuler un functor un argument.|  
  
|Fonction|Description|  
|--------------|-----------------|  
|[bind1st (STL/CLR)](../dotnet/bind1st-stl-clr.md)|Génère un binder1st pour un argument et un functor.|  
|[bind2nd (STL/CLR)](../dotnet/bind2nd-stl-clr.md)|Génère un binder2nd pour un argument et un functor.|  
|[not1 (STL/CLR)](../dotnet/not1-stl-clr.md)|Génère un unary_negate pour un functor.|  
|[not1 (STL/CLR)](../dotnet/not1-stl-clr.md)|Génère un binary_negate pour un functor.|  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/fonctionnel >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de bibliothèque STL/CLR](../dotnet/stl-clr-library-reference.md)