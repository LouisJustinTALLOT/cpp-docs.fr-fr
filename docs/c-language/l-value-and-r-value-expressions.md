---
title: Expressions L-Value et R-Value
ms.date: 11/04/2016
helpviewer_keywords:
- L-values
- member-selection expressions
- R-value expressions
- subscript expressions
ms.assetid: b790303e-ec6f-4d0d-bc55-df42da267172
ms.openlocfilehash: bd5f702588a11b7841f77de539d113206833cde9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325518"
---
# <a name="l-value-and-r-value-expressions"></a>Expressions L-Value et R-Value

Les expressions qui font référence à des emplacements de mémoire sont appelées expressions « l-value ». Une l-value représente la valeur « Localisateur » d’une région de stockage, ou une valeur « gauche », ce qui signifie qu’elle peut apparaître à gauche du signe égal**=**(). Les l-values sont souvent des identificateurs.

Les expressions faisant référence à des emplacements modifiables sont appelées « l-values modifiables ». Une l-value modifiable ne peut pas être définie avec un type de tableau, un type incomplet ou un type avec l’attribut **const**. Pour que les structures et les unions soient des l-values modifiables, elles ne doivent comporter aucun membre défini avec l’attribut **const**. Le nom de l'identificateur désigne un emplacement de stockage, alors que la valeur de la variable est la valeur stockée à cet emplacement.

Un identificateur est une l-value modifiable si elle fait référence à un emplacement mémoire et si son type est arithmétique, structure, union ou pointeur. Par exemple, si `ptr` est un pointeur vers une zone de stockage, `*ptr` est une l-value modifiable qui désigne la zone de stockage vers laquelle `ptr` pointe.

Les expressions C suivantes peuvent être des expressions l-value :

- Un identificateur de type intégral, flottant, pointeur, structure ou union

- Une expression d’indice (**[ ]**) qui ne correspond pas à un tableau

- Une expression de sélection de membres**->** (ou **.**)

- Expression d’indirection unaire (<strong>\*</strong>) qui ne fait pas référence à un tableau

- Une expression l-value entre parenthèses

- Un objet **const** (une l-value non modifiable)

Le terme « r- value » est parfois utilisé pour décrire la valeur d'une expression et pour établir une distinction par rapport à une l-value. Toutes les l-values sont des r- values, mais les r- values ne sont pas toutes des l-values.

**Spécifique à Microsoft**

Microsoft C inclut une extension vers la norme C ANSI qui permet d’effectuer un cast sur des l-values à utiliser en tant que l-values, à condition que la taille de l’objet ne soit pas rallongée lors de cette opération. (Pour plus d’informations, consultez [conversions de cast de type](../c-language/type-cast-conversions.md) .) L’exemple suivant illustre cette fonctionnalité :

```
char *p ;
short  i;
long l;

(long *) p = &l ;       /* Legal cast   */
(long) i = l ;          /* Illegal cast */
```

Par défaut pour Microsoft C, les extensions Microsoft sont activées. Utilisez l’option du compilateur /Za pour désactiver ces extensions.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Opérandes et expressions](../c-language/operands-and-expressions.md)
