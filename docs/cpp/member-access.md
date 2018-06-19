---
title: Accès aux membres | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- member-selection operators [C++]
- pointers, smart
- member access, overloaded operators
- operator overloading [C++], member access operators
- smart pointers, definition
- smart pointers
ms.assetid: 8c7b2c43-eb92-4d42-9a8e-61aa37d71333
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d8896e473f1a419f24636d7c503924b51426be24
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32420082"
---
# <a name="member-access"></a>Accès aux membres
Accès aux membres de classe peut être contrôlé en surchargeant l’opérateur d’accès au membre (**->**). Cet opérateur est considéré comme un opérateur unaire dans cette utilisation, et la fonction surchargée d'opérateur doit être une fonction membre de classe. Par conséquent, la déclaration pour une telle fonction est :  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
class-type *operator->()  
```  
  
## <a name="remarks"></a>Notes  
 où *de type classe* est le nom de la classe à laquelle appartient cet opérateur. La fonction opérateur d'accès au membre doit être une fonction membre non statique.  
  
 Cet opérateur est utilisé (souvent avec l'opérateur pointer-dereference) pour implémenter des « pointeurs intelligents » qui valident les pointeurs avant de déréférencer ou de compter l'utilisation.  
  
 L’élément de langage **.** opérateur d’accès au membre ne peut pas être surchargé.  
  
## <a name="see-also"></a>Voir aussi  
 [Surcharge d'opérateur](../cpp/operator-overloading.md)