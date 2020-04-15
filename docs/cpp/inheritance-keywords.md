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
ms.openlocfilehash: f0aae655540b4d3f9130d9840d77e0abcf270cc2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374104"
---
# <a name="inheritance-keywords"></a>Mots clé d'héritage

**Microsoft Spécifique**

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

Dans le code `p` ci-dessus, est déclaré être un pointeur pour integer membre de la classe S. Toutefois, `class S` ce code n’a pas encore été défini; elle n’a été déclarée. Lorsque le compilateur détecte ce type de pointeur, il doit créer une représentation généralisée du pointeur. La taille de la représentation dépend du modèle d'héritage spécifié. Il existe quatre façons de spécifier un modèle d'héritage au compilateur :

- Dans l’IDE sous **la représentation pointeur-à-membre**

- Sur la ligne de commande à l’aide de l’interrupteur [/vmg](../build/reference/vmb-vmg-representation-method.md)

- Utilisation du [pragma pointers_to_members](../preprocessor/pointers-to-members.md)

- En utilisant les mots-clés de **l’héritage __single_inheritance**, **__multiple_inheritance**, et **__virtual_inheritance**. Cette technique contrôle le modèle d'héritage pour chaque classe.

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

Pour la compatibilité avec les versions précédentes, **_single_inheritance**, **_multiple_inheritance**, et **_virtual_inheritance** sont synonymes pour **__single_inheritance**, **__multiple_inheritance**, et **__virtual_inheritance** à moins que l’option compilateur [/Za \(Désactiver les extensions de langage)](../build/reference/za-ze-disable-language-extensions.md) est spécifiée.

**END Microsoft Spécifique**

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)
