---
description: En savoir plus sur les opérations arithmétiques sur les pointeurs
title: Arithmétique sur les pointeurs
ms.date: 11/04/2016
helpviewer_keywords:
- pointer arithmetic
- arithmetic pointer
ms.assetid: eb924a29-59d3-48a5-9d62-9424790730eb
ms.openlocfilehash: 37ee9fd696f874d1faa84b5d656317cf67f75a6c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97243118"
---
# <a name="pointer-arithmetic"></a>Arithmétique sur les pointeurs

Les opérations d’addition impliquant un pointeur et un entier fournissent des résultats significatifs uniquement si l’opérande de pointeur adresse un membre de tableau et si la valeur entière produit un décalage dans les limites du même tableau. Lorsque la valeur entière est convertie en décalage d'adresse, le compilateur suppose que seules les positions de mémoire de même taille figurent entre l'adresse d'origine et l'adresse plus le décalage.

Cette hypothèse est valide pour les membres de tableau. Par définition, un tableau est une série de valeurs du même type ; ses éléments résident dans des emplacements de mémoire contigus. Toutefois, il n'est pas garanti que le stockage pour les types autres que les éléments de tableau soient remplis par le même type d'identificateurs. Autrement dit, des vides peuvent apparaître entre les positions de mémoire, même les positions de même type. Par conséquent, les résultats de l'ajout ou de la soustraction des adresses de toute valeur autre que des éléments de tableau sont non définis.

De même, lorsque deux valeurs de type pointeur sont soustraites, la conversion suppose que seules des valeurs du même type, sans vides, résident entre les adresses données par les opérandes.

## <a name="see-also"></a>Voir aussi

[Opérateurs additifs C](../c-language/c-additive-operators.md)
