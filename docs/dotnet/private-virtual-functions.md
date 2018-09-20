---
title: Fonctions virtuelles privées | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- virtual functions, private
- derived classes, virtual functions
- access modifiers [C++], for class members
- member access [C++], virtual members
ms.assetid: 04448086-bf72-44be-9c1f-dfda1744949e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0058d023268fa4d9ca5abe802ff45856e9855dc7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418071"
---
# <a name="private-virtual-functions"></a>Fonctions virtuelles privées

Les fonctions virtuelles privées sont gérées dans les classes dérivées a été modifiée à partir des Extensions managées pour C++ vers Visual C++.

Dans les Extensions managées, le niveau d’accès d’une fonction virtuelle ne limite pas sa capacité à être substituée dans une classe dérivée. Dans la nouvelle syntaxe, une fonction virtuelle ne peut pas substituer une fonction virtuelle de classe de base qui ne peut pas accéder. Exemple :

```
__gc class MyBaseClass {
   // inaccessible to a derived class
   virtual void g();
};

__gc class MyDerivedClass : public MyBaseClass {
public:
   // okay in Managed Extensions; g() overrides MyBaseClass::g()
   // error in new syntax; cannot override: MyBaseClass::g() is inaccessible
   void g();
};
```

Il n’existe aucun mappage de ce type dans la nouvelle syntaxe. Un a simplement rendre les membres de classe de base accessible - autrement dit, non privée. Méthodes héritées n’est pas ont de porter le même accès. Dans cet exemple, la modification la moins importante consiste à rendre le membre de MyBaseClass `protected`. De cette façon accès du programme général à la méthode via MyBaseClass est toujours interdit.

```
ref class MyBaseClass {
protected:
   virtual void g();
};

ref class MyDerivedClass : MyBaseClass {
public:
   virtual void g() override;
};
```

Notez que l’absence d’explicites `virtual` mot clé dans la classe de base, sous la nouvelle syntaxe, génère un message d’avertissement.

## <a name="see-also"></a>Voir aussi

[Déclarations de membre dans une classe ou interface (C++-CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)
