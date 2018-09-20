---
title: Sceller une fonction virtuelle | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sealed keyword [C++]
- derived classes, virtual functions
- virtual functions, sealing
- __sealed keyword
ms.assetid: 0e9fae03-6425-4512-9a24-8ccb6dc8a0d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 69ac614d55ade10b94621da2a3eb1c43d25ebaf5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385181"
---
# <a name="sealing-a-virtual-function"></a>Sceller une fonction virtuelle

La syntaxe pour sceller une fonction virtuelle a changé d’Extensions managées pour C++ vers Visual C++.

Le `__sealed` mot clé est utilisé dans les Extensions managées à modifier soit un type référence, en interdisant les dérivations suivantes (voir [déclaration d’un Type de classe gérée](../dotnet/declaration-of-a-managed-class-type.md)), ou pour modifier une fonction virtuelle, interdiction substitution suivante de la méthode dans une classe dérivée. Exemple :

```
__gc class base { public: virtual void f(); };
__gc class derived : public base {
public:
   __sealed void f();
};
```

Dans cet exemple, `derived::f()` remplace le `base::f()` basé sur une instance de la correspondance exacte du prototype de fonction. Le `__sealed` mot-clé indique qu’une classe suivante héritée de la classe dérivée ne peut pas fournir une substitution de `derived::f()`.

Dans la nouvelle syntaxe, `sealed` est placé après la signature au lieu d’être autorisé à apparaître avant le prototype de fonction réelle, comme il était auparavant autorisée. En outre, l’utilisation de `sealed` requiert l’utilisation explicite de la `virtual` mot clé également. Autrement dit, la traduction de `derived`, ci-dessus, est la suivante :

```
ref class derived: public base {
public:
   virtual void f() override sealed;
};
```

L’absence de la `virtual` mot clé dans cette instance entraîne une erreur. Dans la nouvelle syntaxe, le mot clé contextuel `abstract` peut être utilisé à la place de la `=0` pour indiquer une fonction virtuelle pure. Cela n’était pas pris en charge dans les Extensions managées. Exemple :

```
__gc class base { public: virtual void f()=0; };
```

peut être réécrite en tant que

```
ref class base { public: virtual void f() abstract; };
```

## <a name="see-also"></a>Voir aussi

[Déclarations de membre dans une classe ou interface (C++-CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)<br/>
[sealed](../windows/sealed-cpp-component-extensions.md)