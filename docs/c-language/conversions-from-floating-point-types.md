---
title: Conversions depuis les types à virgule flottante
ms.date: 10/02/2019
helpviewer_keywords:
- converting floating point
- floating-point conversion
ms.assetid: 96804c8e-fa3b-4742-9006-0082ed9e57f2
ms.openlocfilehash: c2f7c25015b36545f969796a1f85d355d715427a
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998718"
---
# <a name="conversions-from-floating-point-types"></a>Conversions depuis les types à virgule flottante

Une valeur à virgule flottante qui est convertie en un autre type à virgule flottante ne subit aucune modification dans la valeur si la valeur d’origine est représentable exactement dans le type de résultat. Si la valeur d’origine est numérique mais n’est pas représentable exactement, le résultat est la valeur représentable supérieure ou inférieure suivante. Consultez [limites sur les constantes à virgule flottante](../c-language/limits-on-floating-point-constants.md) pour la plage de types à virgule flottante.

Une valeur à virgule flottante qui est convertie en un type intégral est d’abord tronquée en ignorant toute valeur fractionnaire. Si cette valeur tronquée est représentable dans le type de résultat, le résultat doit être cette valeur. Lorsqu’il n’est pas représentable, la valeur de résultat n’est pas définie.

**Section spécifique à Microsoft**

Les compilateurs Microsoft utilisent la représentation IEEE-754 binary32 pour les valeurs **float** et la représentation binary64 pour **long double** et **double**. Étant donné que les valeurs **long double** et **double** utilisent la même représentation, elles ont la même plage et la même précision.

Lorsque le compilateur convertit un nombre à virgule flottante **double** ou **long** en **un nombre**à virgule flottante, il arrondit le résultat en fonction des contrôles d’environnement à virgule flottante, qui sont par défaut «arrondis au plus près). Si une valeur numérique est trop élevée ou trop faible pour être représentée sous la forme d’une valeur **flottante** numérique, le résultat de la conversion est un infini positif ou négatif en fonction du signe de la valeur d’origine, et une exception de dépassement de capacité est levée, si elle est activée.

Lors de la conversion en types entiers, le résultat d’une conversion vers un type plus petit que **long** est le résultat de la conversion de la valeur en **long**, puis de la conversion vers le type de résultat.

Pour la conversion en types entiers au moins aussi grand que **long**, une conversion d’une valeur trop élevée ou trop faible pour être représentée dans le type de résultat peut retourner l’une des valeurs suivantes :

- Le résultat peut être une *valeur de sentinelle*, qui est la valeur représentable la plus éloignée de zéro. Pour les types signés, il s’agit de la valeur représentable la plus faible (0x800... 0). Pour les types non signés, il s’agit de la valeur représentable la plus élevée (0xFF... F).

- Le résultat peut être *saturé*, où les valeurs trop élevées pour être représentées sont converties en valeur représentable la plus élevée, et les valeurs trop basses pour être représentées sont converties en valeur représentable la plus basse. L’une de ces deux valeurs est également utilisée comme valeur de sentinelle.

- Pour la conversion en type **unsigned** long ou **unsigned long long**, le résultat de la conversion d’une valeur hors limites peut être une valeur autre que la valeur représentable la plus élevée ou la plus basse. Le fait que le résultat soit une valeur Sentinel ou saturée dépend des options du compilateur et de l’architecture cible. Les futures versions du compilateur peuvent retourner une valeur saturée ou Sentinel à la place.

**FIN de la section spécifique à Microsoft**

Le tableau suivant répertorie les conversions des types de flottant.

## <a name="table-of-conversions-from-floating-point-types"></a>Table des conversions des types à virgule flottante

|From|À|Méthode|
|----------|--------|------------|
|**float**|**char**|Convertir en **long**. Convertir **long** en **char**|
|**float**|**short**|Convertir en **long**. Convertir **long** en **short**|
|**float**|**int**|Tronquer à la virgule décimale. Si le résultat est trop grand pour être représenté sous la forme **int**, le résultat n’est pas défini.|
|**float**|**long**|Tronquer à la virgule décimale. Si le résultat est trop grand pour être représenté comme **long**, il n'est pas défini.|
|**float**|**long long**|Tronquer à la virgule décimale. Si le résultat est trop grand pour être représenté comme **long long**, le résultat n’est pas défini.|
|**float**|**unsigned char**|Convertir en **long**; convertir **long** en **char non signé**|
|**float**|**unsigned short**|Convertir en **long**. Convertir **long** en **unsigned short**|
|**float**|**unsigned**|Tronquer à la virgule décimale. Si le résultat est trop grand pour être représenté comme **non signé**, le résultat n’est pas défini.|
|**float**|**unsigned long**|Tronquer à la virgule décimale. Si le résultat est trop grand pour être représenté comme **unsigned long**, le résultat n’est pas défini.|
|**float**|**long long non signé**|Tronquer à la virgule décimale. Si le résultat est trop grand pour être représenté comme **unsigned long long**, le résultat n’est pas défini.|
|**float**|**double**|Représente un **double**.|
|**float**|**long double**|Représente une **valeur de type long double**.|
|**double**|**char**|Convertir en **float**. Convertir **float** en **char**|
|**double**|**short**|Convertir en **float**. Convertir **float** en **short**|
|**double**|**int**|Tronquer à la virgule décimale. Si le résultat est trop grand pour être représenté sous la forme **int**, le résultat n’est pas défini.|
|**double**|**long**|Tronquer à la virgule décimale. Si le résultat est trop grand pour être représenté comme **long**, il n'est pas défini.|
|**double**|**unsigned char**|Convertir en **long**; convertir **long** en **char non signé**|
|**double**|**unsigned short**|Convertir en **long**. Convertir **long** en **unsigned short**|
|**double**|**unsigned**|Tronquer à la virgule décimale. Si le résultat est trop grand pour être représenté comme **non signé**, le résultat n’est pas défini.|
|**double**|**unsigned long**|Tronquer à la virgule décimale. Si le résultat est trop grand pour être représenté comme **unsigned long**, le résultat n’est pas défini.|
|**double**|**long long non signé**|Tronquer à la virgule décimale. Si le résultat est trop grand pour être représenté comme **unsigned long long**, le résultat n’est pas défini.|
|**double**|**float**|Représenter comme **float**. Si la valeur **double** ne peut pas être représentée exactement comme **float**, une perte de précision se produit. Si la valeur est trop grande pour être représentée comme **float**, le résultat n'est pas défini.|
|**double**|**long double**|La valeur **long double** est traitée comme **double**.|

Les conversions de **long double** suivent la même méthode que les conversions de **double**.

## <a name="see-also"></a>Voir aussi

[Conversions d’assignation](../c-language/assignment-conversions.md)
