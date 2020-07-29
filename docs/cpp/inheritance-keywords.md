---
title: Mots clé d'héritage
ms.date: 11/04/2016
f1_keywords:
- __multiple_inheritance
- __single_inheritance_cpp
- __virtual_inheritance_cpp
- __virtual_inheritance
- __multiple_inheritance_cpp
- __single_inheritance
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
ms.openlocfilehash: bc9afdcb7971c478c1cad9185cece57ea6326a48
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233728"
---
# <a name="inheritance-keywords"></a>Mots clé d'héritage

**Spécifique à Microsoft**

```
class [__single_inheritance] class-name;
class [__multiple_inheritance] class-name;
class [__virtual_inheritance] class-name;
```

où :

*nom de classe*<br/>
est le nom de la variable en cours de déclaration.

C++ vous permet de déclarer un pointeur vers un membre de classe avant la définition de la classe. Par exemple :

```cpp
class S;
int S::*p;
```

Dans le code ci-dessus, `p` est déclaré comme étant un pointeur vers un membre entier de classe S. Toutefois, n' `class S` a pas encore été défini dans ce code ; il a été déclaré uniquement. Lorsque le compilateur détecte ce type de pointeur, il doit créer une représentation généralisée du pointeur. La taille de la représentation dépend du modèle d'héritage spécifié. Il existe quatre façons de spécifier un modèle d'héritage au compilateur :

- Dans l’IDE, sous la **représentation pointeur vers membre**

- Au niveau de la ligne de commande à l’aide du commutateur [/VMG](../build/reference/vmb-vmg-representation-method.md)

- Utilisation du pragma [pointers_to_members](../preprocessor/pointers-to-members.md)

- À l’aide des mots clés d’héritage **`__single_inheritance`** , **`__multiple_inheritance`** et **`__virtual_inheritance`** . Cette technique contrôle le modèle d'héritage pour chaque classe.

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
> La même déclaration anticipée d'une représentation de pointeur de classe vers membre devrait se produire dans chaque unité de traduction qui déclare des pointeurs vers des membres de cette classe, et la déclaration devrait se produire avant que les pointeurs vers des membres soient déclarées.

Pour la compatibilité avec les versions précédentes, **_single_inheritance**, **_multiple_inheritance**et **_virtual_inheritance** sont des synonymes de **`__single_inheritance`** , **`__multiple_inheritance`** et, **`__virtual_inheritance`** sauf si l’option de compilateur [/za désactive les extensions de \( langage)](../build/reference/za-ze-disable-language-extensions.md) est spécifiée.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)
