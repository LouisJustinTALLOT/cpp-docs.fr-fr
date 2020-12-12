---
description: 'En savoir plus sur : opérateurs binaires'
title: Opérateurs binaires
ms.date: 06/14/2018
helpviewer_keywords:
- member-selection operators [C++]
- operators [C++], binary
- binary operators [C++]
ms.assetid: c0e7fbff-bc87-4708-8333-504ac09ee83e
ms.openlocfilehash: cfb897a3df7cdb3d76f7af82f694e1cf09284cc7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97229598"
---
# <a name="binary-operators"></a>Opérateurs binaires

Le tableau suivant affiche une liste des opérateurs qui peuvent être surchargés.

## <a name="redefinable-binary-operators"></a>Opérateurs binaires redéfinissables

|Opérateur|Nom|
|--------------|----------|
|**,**|Comma|
|**!=**|Inégalité|
|**%**|Modulo|
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
