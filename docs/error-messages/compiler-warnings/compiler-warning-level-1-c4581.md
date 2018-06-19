---
title: Compilateur avertissement (niveau 1) C4581 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4581
dev_langs:
- C++
helpviewer_keywords:
- C4581
ms.assetid: 598bcd87-257d-4eb3-94e4-15bb31aadc99
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 415fb9ffc3e53ddfe9edcee2ec99361b38de0dea
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33281857"
---
# <a name="compiler-warning-level-1-c4581"></a>Avertissement du compilateur (niveau 1) C4581
comportement déconseillé : '« chaîne1 »' remplacé par 'chaîne2' pour traiter l’attribut  
  
 Cette erreur peut être due à la mise en conformité du compilateur pour Visual C++ 2005 : vérification des paramètres des attributs Visual C++.  
  
 Dans les versions précédentes, les valeurs d’attribut ont été acceptées ou non qu’ils ont été entourées de guillemets. Si la valeur est une énumération, elle ne doit pas figurer entre guillemets.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C4581.  
  
```  
// C4581.cpp  
// compile with: /c /W1  
#include "unknwn.h"  
[object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface IMyI : IUnknown {};  
  
[coclass, uuid(12345678-1111-2222-3333-123456789012), threading("free")]   // C4581  
// try the following line instead  
// [coclass, uuid(12345678-1111-2222-3333-123456789012), threading(free)]  
class CSample : public IMyI {};  
```