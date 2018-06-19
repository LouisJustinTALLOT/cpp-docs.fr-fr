---
title: Compilateur avertissement (niveau 1) C4788 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4788
dev_langs:
- C++
helpviewer_keywords:
- C4788
ms.assetid: 47d75bda-f833-4bdd-93a0-a134df0cd303
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 19a43fb9d79c63637b2bff9a27661a9f848ef6dc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33284197"
---
# <a name="compiler-warning-level-1-c4788"></a>Avertissement du compilateur (niveau 1) C4788
'identificateur' : identificateur tronqué à 'nombre' caractères  
  
 Le compilateur limite la longueur maximale autorisée pour un nom de fonction. Lorsque le compilateur génère des funclets pour le code EH/SEH, il constitue le nom funclet en ajoutant le nom de fonction avec du texte, par exemple « __catch, » «\__unwind », ou une autre chaîne.  
  
 Le nom de funclet résultant peut être trop long, et le compilateur sera tronqué et générer C4788.  
  
 Pour résoudre cet avertissement, raccourcissez le nom de fonction d’origine. Si la fonction est une fonction de modèle C++ ou une méthode, utilisez un typedef pour une partie du nom. Par exemple :  
  
```  
C1<x, y, z<T>>::C2<a,b,c>::f  
```  
  
 peut être remplacé par :  
  
```  
typedef C1<x, y, z<T>>::C2<a,b,c> new_class ;  
new_class::f  
```  
  
 Cet avertissement se produit uniquement dans le [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] compilateur.