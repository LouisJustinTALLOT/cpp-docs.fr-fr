---
title: Erreur du compilateur C3675 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3675
dev_langs:
- C++
helpviewer_keywords:
- C3675
ms.assetid: 87461613-6633-430b-b95d-c7cb1bb63776
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1b4aaa53ae1d92364fad143f127ee3e7b504acdd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273642"
---
# <a name="compiler-error-c3675"></a>Erreur du compilateur C3675
'fonction' : est réservé, car 'propriété' est définie.  
  
 Lorsque vous déclarez une propriété simple, le compilateur génère get et méthodes d’accesseur set et ces noms sont présents dans la portée de votre programme.  Les noms générés par le compilateur sont constitués en ajoutant get_ et set_ au nom de propriété.  Par conséquent, vous ne pouvez pas déclarer des fonctions avec le même nom que les accesseurs générés par le compilateur.  
  
 Pour plus d'informations, voir [property](../../windows/property-cpp-component-extensions.md) .  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C3675.  
  
```  
// C3675.cpp  
// compile with: /clr /c  
ref struct C {  
public:  
   property int Size;  
   int get_Size() { return 0; }   // C3675  
};  
```