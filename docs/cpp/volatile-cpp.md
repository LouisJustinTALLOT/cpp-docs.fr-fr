---
title: volatile (C++)
ms.date: 05/07/2019
f1_keywords:
- volatile_cpp
helpviewer_keywords:
- interrupt handlers and volatile keyword [C++]
- volatile keyword [C++]
- volatile objects
- objects [C++], volatile
ms.assetid: 81db4a85-ed5a-4a2c-9a53-5d07a771d2de
ms.openlocfilehash: 841b2e1e4ffbec87a170c45be8ad0cd0f831a0ef
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371897"
---
# <a name="volatile-c"></a>volatile (C++)

Qualificateur de type que vous pouvez utiliser pour déclarer qu'un objet peut être modifié dans le programme par le matériel.

## <a name="syntax"></a>Syntaxe

```
volatile declarator ;
```

## <a name="remarks"></a>Notes

Vous pouvez utiliser le [compilateur/volatil](../build/reference/volatile-volatile-keyword-interpretation.md) compilateur pour modifier la façon dont le compilateur interprète ce mot clé.

Visual Studio interprète le mot clé **volatil** différemment selon l’architecture cible. Pour ARM, si aucune option de compilateur **/volatil** n’est spécifiée, le compilateur effectue comme si **/volatile:iso** ont été spécifiés. Pour les architectures autres que ARM, si aucune option de compilateur **/volatile** n’est spécifiée, le compilateur effectue comme si **/volatile:ms** ont été spécifiés; par conséquent, pour des architectures autres que ARM nous vous recommandons fortement de spécifier **/volatile:iso**, et d’utiliser des primitifs de synchronisation explicite et des intrinsèques compilateur lorsque vous avez affaire à la mémoire qui est partagée entre les fils.

Vous pouvez utiliser le qualificatif **volatil** pour donner accès à des endroits de mémoire qui sont utilisés par des processus asynchrones tels que les gestionnaires d’interruption.

Lorsque **volatile** est utilisé sur une variable qui a également le mot clé [__restrict,](../cpp/extension-restrict.md) **volatile** a préséance.

Si un membre **structurant** est marqué comme **volatil,** alors **volatile** est propagé à l’ensemble de la structure. Si une structure n’a pas une longueur qui peut être copiée sur l’architecture actuelle en utilisant une instruction, **volatile** peut être complètement perdu sur cette structure.

Le mot clé **volatil** peut n’avoir aucun effet sur un champ si l’une des conditions suivantes est vraie :

- La longueur du champ volatile dépasse la taille maximale pouvant être copiée sur l'architecture actuelle en utilisant une instruction.

- La longueur de la **structure**la plus externe , ou si elle est membre d’une struct éventuellement **imbriquée,** dépasse la taille maximale qui peut être copiée sur l’architecture actuelle en utilisant une instruction.

Bien que le processeur ne réorganise pas les accès à la mémoire indétables, les variables in-cacheables doivent être marquées comme **volatiles** pour garantir que le compilateur ne réorganise pas les accès à la mémoire.

Les objets déclarés **volatils** ne sont pas utilisés dans certaines optimisations parce que leurs valeurs peuvent changer à tout moment.  Le système lit toujours la valeur actuelle d'un objet volatile lorsque la demande en est faite, même si une instruction précédente a demandé une valeur du même objet.  De même, la valeur de l'objet est écrite immédiatement sur l'assignation.

## <a name="iso-compliant"></a>Conformité ISO

Si vous connaissez le mot clé volatil CMD, ou si vous connaissez le comportement de **volatile** dans les versions antérieures du compilateur Microsoft CMD (MSVC), sachez que le mot clé **volatil** ISO Standard de C-11 est différent et est pris en charge dans MSVC lorsque l’option de compilateur [iso /volatile :](../build/reference/volatile-volatile-keyword-interpretation.md) est spécifiée. (Pour ARM, elle est spécifiée par défaut). Le mot clé **volatil** dans le code ISO Standard de C-11 ne doit être utilisé que pour l’accès matériel ; ne l’utilisez pas pour la communication inter-thread. Pour la communication inter-thread, utiliser des mécanismes tels que [std::atomic\<T>](../standard-library/atomic.md) de la Bibliothèque standard C [.](../standard-library/cpp-standard-library-reference.md)

## <a name="end-of-iso-compliant"></a>Fin de la conformité ISO

**Microsoft Spécifique**

Lorsque l’option **compilateur /volatile:ms** est utilisée, par défaut lorsque des architectures autres qu’ARM sont ciblées, le compilateur génère du code supplémentaire pour maintenir la commande parmi les références à des objets volatils en plus de maintenir la commande à des références à d’autres objets mondiaux. En particulier :

- L’écriture dans un objet volatile (également appelée "écriture volatile") a une sémantique Release, c’est-à-dire, une référence à un objet global ou statique qui se produit avant qu’une écriture dans un objet volatile de la séquence d’instructions ne se produise avant cette écriture volatile dans le fichier binaire compilé.

- La lecture d'un objet volatile (également appelée "lecture volatile") a une sémantique Acquire, c'est-à-dire, une référence à un objet global ou statique qui se produit après qu'une lecture de la mémoire volatile dans la séquence d'instructions se produit après cette lecture volatile dans le fichier binaire compilé.

Cela permet aux objets volatiles d'être utilisés pour les verrous et les libérations de mémoire dans les applications multithread.

> [!NOTE]
> Lorsqu’il s’appuie sur la garantie améliorée qui est fournie lorsque l’option de compilateur **/volatile:ms** est utilisée, le code n’est pas portable.

**END Microsoft Spécifique**

## <a name="see-also"></a>Voir aussi

[Mots clés](../cpp/keywords-cpp.md)<br/>
[const](../cpp/const-cpp.md)<br/>
[const et volatile Pointeurs](../cpp/const-and-volatile-pointers.md)
