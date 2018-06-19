---
title: numérique (STL/CLR) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- <cliext/numeric>
dev_langs:
- C++
helpviewer_keywords:
- numeric functions [STL/CLR]
- <cliext/numeric> header [STL/CLR]
- <numeric> header [STL/CLR]
ms.assetid: 1dc4d9a3-e734-459c-9678-5d9be0ef4c79
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8d02423b2f8a2573fb4a90fd6f348a8e012dc91b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33139524"
---
# <a name="numeric-stlclr"></a>numériques (STL/CLR)
Définit les fonctions de modèle de conteneur qui exécutent des algorithmes fournis pour le traitement numérique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#include <cliext/numeric>  
```  
  
## <a name="functions"></a>Fonctions  
  
|Fonction|Description|  
|--------------|-----------------|  
|[accumulate (STL/CLR)](../dotnet/accumulate-stl-clr.md)|Calcule la somme de tous les éléments d’une plage spécifiée incluant une valeur initiale en calculant des sommes partielles successives, ou calcule le résultat des résultats partiels successifs obtenus de la même façon en utilisant une opération binaire spécifiée autre que la somme.|  
|[adjacent_difference (STL/CLR)](../dotnet/adjacent-difference-stl-clr.md)|Détermine les différences successives entre chaque élément et son prédécesseur au sein d'une plage d'entrée, puis génère les résultats dans une plage de destination ou calcule le résultat d'une procédure généralisée dans laquelle l'opération de différence est remplacée par une autre opération binaire spécifiée.|  
|[inner_product (STL/CLR)](../dotnet/inner-product-stl-clr.md)|Calcule la somme du produit d’éléments de deux plages et l’ajoute à une valeur initiale spécifiée, ou calcule le résultat d’une procédure généralisée dans laquelle les opérations binaires de somme et de produit sont remplacées par d’autres opérations binaires spécifiées.|  
|[partial_sum (STL/CLR)](../dotnet/partial-sum-stl-clr.md)|Calcule une série de sommes dans une plage d’entrée du premier élément via le `i`élément th et stocke le résultat de chaque somme dans `i`ième élément d’une plage de destination ou calcule le résultat d’une procédure généralisée où l’opération de somme est remplacé par une autre opération binaire spécifiée.|  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** \<cliext/numeric >  
  
 **Namespace :** cliext  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de bibliothèque STL/CLR](../dotnet/stl-clr-library-reference.md)