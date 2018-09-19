---
title: Mots clés d’héritage | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __multiple_inheritance
- __single_inheritance_cpp
- __virtual_inheritance_cpp
- __virtual_inheritance
- __multiple_inheritance_cpp
- __single_inheritance
dev_langs:
- C++
helpviewer_keywords:
- __single_inheritance keyword [C++]
- declaring derived classes [C++]
- keywords [C++], inheritance keywords
- __multiple_inheritance keyword [C++]
- __virtual_inheritance keyword [C++]
- inheritance, declaring derived classes
- derived classes [C++], declaring
- inheritance, keywords
ms.assetid: bb810f56-7720-4fea-b8b6-9499edd141df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1106ad878f4053cacae67d9d0e343e9469b1a1c1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061173"
---
# <a name="inheritance-keywords"></a>Mots clé d'héritage

**Section spécifique à Microsoft**

```
class [__single_inheritance] class-name;
class [__multiple_inheritance] class-name;
class [__virtual_inheritance] class-name;
```

où :

*nom de la classe*<br/>
est le nom de la variable en cours de déclaration.

C++ vous permet de déclarer un pointeur vers un membre de classe avant la définition de la classe. Exemple :

```cpp
class S;
int S::*p;
```

Dans le code ci-dessus, `p` est déclaré comme étant un pointeur vers membre entier de la classe S. Toutefois, `class S` a ne pas encore été défini dans ce code ; il a uniquement été déclaré. Lorsque le compilateur détecte ce type de pointeur, il doit créer une représentation généralisée du pointeur. La taille de la représentation dépend du modèle d'héritage spécifié. Il existe quatre façons de spécifier un modèle d'héritage au compilateur :

- Dans l’IDE sous **représentation de pointeur vers membre**

- À la ligne de commande à l’aide de la [/vmg](../build/reference/vmb-vmg-representation-method.md) basculer

- À l’aide de la [pointers_to_members](../preprocessor/pointers-to-members.md) (pragma)

- À l’aide de mots clés d’héritage **__single_inheritance**, **__multiple_inheritance**, et **__virtual_inheritance**. Cette technique contrôle le modèle d'héritage pour chaque classe.

    > [!NOTE]
    >  Si vous déclarez toujours un pointeur vers un membre d'une classe après la définition de la classe, vous n'avez pas besoin d'utiliser l'une de ces options.

La déclaration d'un pointeur vers un membre d'une classe avant la définition de classe a une incidence sur la taille et la vitesse du fichier exécutable résultant. Plus l'héritage utilisé par une classe est complexe, plus le nombre d'octets requis pour représenter un pointeur vers un membre de la classe est élevé et plus le code nécessaire pour interpréter le pointeur est volumineux. L'héritage unique est moins complexe, et l'héritage virtuel est plus complexe.

Si l'exemple ci-dessus est modifié comme suit :

```cpp
class __single_inheritance S;
int S::*p;
```

indépendamment des options de ligne de commande ou des pragmas, les pointeurs vers des membres de `class S` utiliseront la plus petite représentation possible.

> [!NOTE]
>  La même déclaration anticipée d'une représentation de pointeur de classe vers membre devrait se produire dans chaque unité de traduction qui déclare des pointeurs vers des membres de cette classe, et la déclaration devrait se produire avant que les pointeurs vers des membres soient déclarées.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)