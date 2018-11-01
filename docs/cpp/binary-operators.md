---
title: Opérateurs binaires
ms.date: 06/14/2018
helpviewer_keywords:
- member-selection operators [C++]
- operators [C++], binary
- binary operators [C++]
ms.assetid: c0e7fbff-bc87-4708-8333-504ac09ee83e
ms.openlocfilehash: 700d8fd784862c3e9f81fcde839063ff0a4696bb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602404"
---
# <a name="binary-operators"></a>Opérateurs binaires

Le tableau suivant affiche une liste des opérateurs qui peuvent être surchargés.

## <a name="redefinable-binary-operators"></a>Opérateurs binaires redéfinissables

|Opérateur|Name|
|--------------|----------|
|**,**|Virgule|
|**\!=**|Inégalité|
|**%**|Modulo|
|**%=**|Modulo/assignation|
|**&**|Opération de bits AND|
|**&&**|AND logique|
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
|**=**|Attribution|
|**==**|Égalité|
|**>**|Supérieur à|
|**>=**|Supérieur ou égal à|
|**>>**|Décalage vers la droite|
|**>>=**|Décalage vers la droite/assignation|
|**^**|OR exclusive|
|**^=**|OR exclusive/assignation|
|**&#124;**|Opération de bits OR inclusive|
|**&#124;=**|OR inclusive au niveau du bit/assignation|
|**&#124;&#124;**|OR logique|

Pour déclarer une fonction d'opérateur binaire en tant que membre non statique, vous devez la déclarer comme suit :

> *RET-type* **opérateur** *op* **(** *arg* **)**

où *ret-type* est le type de retour, *op* est un des opérateurs répertoriés dans le tableau précédent, et *arg* est un argument de n’importe quel type.

Pour déclarer une fonction d'opérateur binaire en tant que fonction globale, vous devez la déclarer comme suit :

> *RET-type* **opérateur** *op* **(** _arg1_**,** _arg2_ **)**

où *ret-type* et *op* sont celles décrites pour les fonctions d’opérateur de membre et *arg1* et *arg2* sont des arguments. Au moins un des arguments doit être de type classe.

> [!NOTE]
> Il n’existe aucune restriction sur les types de retour des opérateurs binaires. En revanche, la plupart des opérateurs binaires définis par l’utilisateur retournent un type de classe ou une référence à un type de classe.

## <a name="see-also"></a>Voir aussi

[Surcharge d'opérateur](../cpp/operator-overloading.md)