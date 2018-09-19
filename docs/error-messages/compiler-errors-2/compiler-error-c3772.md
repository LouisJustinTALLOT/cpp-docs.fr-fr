---
title: Erreur du compilateur C3772 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3772
dev_langs:
- C++
helpviewer_keywords:
- C3772
ms.assetid: 63e938d4-088d-41cc-a562-5881a05b5710
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: db40c71001e34cc24c19410006cd39f658718c14
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048758"
---
# <a name="compiler-error-c3772"></a>Erreur du compilateur C3772

"name" : déclaration de modèle friend non valide

La déclaration d’une fonction friend d’une spécialisation de modèle de classe n’est pas autorisée. Vous ne pouvez pas déclarer de spécialisation explicite ou partielle d’un modèle de classe et déclarer, dans la même instruction, une fonction friend de cette spécialisation. L’espace réservé *name* identifie la déclaration non valide.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Ne déclarez pas une fonction friend d’une spécialisation de modèle de classe.

- Si cela est adapté à votre application, déclarez une fonction friend du modèle de classe ou déclarez une fonction friend d’une spécialisation partielle ou explicite particulière.

## <a name="example"></a>Exemple

L’exemple de code suivant échoue, car il déclare une fonction friend d’une spécialisation partielle d’un modèle de classe.

```cpp
// c3772.cpp
// compile with: /c

// A class template.
    template<class T> class A {};

// A partial specialization of the class template.
    template<class T> class A<T*> {};

// An explicit specialization.
    template<> class A<char>;

class X {
// Invalid declaration of a friend of a partial specialization.
    template<class T> friend class A<T*>; // C3772

// Instead, if it is appropriate for your application, declare a
// friend of the class template. Consequently, all specializations
// of the class template are friends:
//    template<class T> friend class A;
// Or declare a friend of a particular partial specialization:
//    friend class A<int*>;
// Or declare a friend of a particular explicit specialization:
//    friend class A<char>;
};
```

## <a name="see-also"></a>Voir aussi

[Modèles](../../cpp/templates-cpp.md)<br/>
[Spécialisation de modèle](../../cpp/template-specialization-cpp.md)
