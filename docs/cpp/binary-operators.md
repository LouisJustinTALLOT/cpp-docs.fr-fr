---
title: Opérateurs binaires
ms.date: 06/14/2018
helpviewer_keywords:
- member-selection operators [C++]
- operators [C++], binary
- binary operators [C++]
ms.assetid: c0e7fbff-bc87-4708-8333-504ac09ee83e
ms.openlocfilehash: f44217b68f6700603218c6f4f3e846075b7e7d55
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229127"
---
# <a name="binary-operators"></a>Opérateurs binaires

Le tableau suivant affiche une liste des opérateurs qui peuvent être surchargés.

## <a name="redefinable-binary-operators"></a>Opérateurs binaires redéfinissables

|Opérateur|Nom|
|--------------|----------|
|**,**|Comma|
|**!=**|Inégalité|
|**%**|Modulus|
|**%=**|Modulo/assignation|
|**&**|ET au niveau du bit|
|**&&**|ET logique|
|**&=**|Opération de bits AND/assignation|
|**&#42;**|Multiplication|
|**&#42;=**|Multiplication/assignation|
|**+**|Addition|
|**+=**|Addition/assignation|
|**-**|Soustraction|
|**-=**|Soustraction/assignation|
|**->**|Sélection de membres|
|**->&#42;**|Sélection de pointeur de membre|
|**/**|Division|
|**/=**|Division/assignation|
|**<**|Inférieur à|
|**<<**|Décalage vers la gauche|
|**<<=**|Décalage vers la gauche/assignation|
|**<=**|Inférieur ou égal à|
|**=**|Affectation|
|**==**|Égalité|
|**>**|Supérieur à|
|**>=**|Supérieur ou égal à|
|**>>**|Décalage vers la droite|
|**>>=**|Décalage vers la droite/assignation|
|**^**|OR exclusive|
|**^=**|OR exclusive/assignation|
|**&#124;**|Opération OR inclusive au niveau du bit|
|**&#124;=**|OR inclusive au niveau du bit/assignation|
|**&#124;&#124;**|OU logique|

Pour déclarer une fonction d'opérateur binaire en tant que membre non statique, vous devez la déclarer comme suit :

> *RET-type* **`operator`** *op* **(** *arg* **)**

où *RET-type* est le type de retour, *op* est l’un des opérateurs listés dans le tableau précédent et *arg* est un argument de n’importe quel type.

Pour déclarer une fonction d'opérateur binaire en tant que fonction globale, vous devez la déclarer comme suit :

> *RET-type* **`operator`** *op* **(** _Arg1_**,** _Arg2_ **)**

où *RET-type* et *op* sont décrits pour les fonctions d’opérateur de membre et *Arg1* et *Arg2* sont des arguments. Au moins un des arguments doit être de type classe.

> [!NOTE]
> Il n’existe aucune restriction sur les types de retour des opérateurs binaires. En revanche, la plupart des opérateurs binaires définis par l’utilisateur retournent un type de classe ou une référence à un type de classe.

## <a name="see-also"></a>Voir aussi

[Surcharge d’opérateur](../cpp/operator-overloading.md)
