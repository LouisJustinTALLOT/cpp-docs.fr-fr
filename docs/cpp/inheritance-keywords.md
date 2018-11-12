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
ms.openlocfilehash: 656ee7ed38c24c9f3b8881f84d8e33ca81e3d936
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462970"
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

Pour assurer la compatibilité avec les versions précédentes, **_single_inheritance**, **_multiple_inheritance**, et **_virtual_inheritance** sont synonymes de **__ héritage unique**, **__multiple_inheritance**, et **__virtual_inheritance** , sauf si option du compilateur [/Za \(désactiver langue Extensions)](../build/reference/za-ze-disable-language-extensions.md) est spécifié.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)