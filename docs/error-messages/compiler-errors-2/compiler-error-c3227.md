---
title: Erreur du compilateur C3227 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3227
dev_langs:
- C++
helpviewer_keywords:
- C3227
ms.assetid: 7939c23a-96c8-43c2-89e9-f217d132d155
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ddf2ec945a8bdbe103631d8346641e1370eda216
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096624"
---
# <a name="compiler-error-c3227"></a>Erreur du compilateur C3227

'paramètre' : ne peut pas utiliser 'mot_clé' pour allouer un type générique

Afin d’instancier un type, un constructeur approprié est nécessaire. Toutefois, le compilateur n’est pas en mesure de garantir qu’un constructeur approprié est disponible.

Vous pouvez utiliser des modèles plutôt que des génériques pour résoudre cette erreur, ou vous pouvez utiliser une des méthodes pour créer une instance du type.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3227 :.

```
// C3227.cpp
// compile with: /clr /c
generic<class T> interface class ICreate {
   static T Create();
};

generic <class T>
where T : ICreate<T>
ref class C {
   void f() {
      T t = new T;   // C3227

      // OK
      T t2 = ICreate<T>::Create();
      T t3 = safe_cast<T>( System::Activator::CreateInstance(T::typeid) );
   }
};
```