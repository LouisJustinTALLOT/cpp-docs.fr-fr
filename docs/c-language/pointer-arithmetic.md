---
title: Arithmétique sur les pointeurs | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- pointer arithmetic
- arithmetic pointer
ms.assetid: eb924a29-59d3-48a5-9d62-9424790730eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fd80fd88a5924cbedf9a07ee700f16c65b66672f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46020145"
---
# <a name="pointer-arithmetic"></a>Arithmétique sur les pointeurs

Les opérations d’addition impliquant un pointeur et un entier fournissent des résultats significatifs uniquement si l’opérande de pointeur adresse un membre de tableau et si la valeur entière produit un décalage dans les limites du même tableau. Lorsque la valeur entière est convertie en décalage d'adresse, le compilateur suppose que seules les positions de mémoire de même taille figurent entre l'adresse d'origine et l'adresse plus le décalage.

Cette hypothèse est valide pour les membres de tableau. Par définition, un tableau est une série de valeurs du même type ; ses éléments résident dans des emplacements de mémoire contigus. Toutefois, il n'est pas garanti que le stockage pour les types autres que les éléments de tableau soient remplis par le même type d'identificateurs. Autrement dit, des vides peuvent apparaître entre les positions de mémoire, même les positions de même type. Par conséquent, les résultats de l'ajout ou de la soustraction des adresses de toute valeur autre que des éléments de tableau sont non définis.

De même, lorsque deux valeurs de type pointeur sont soustraites, la conversion suppose que seules des valeurs du même type, sans vides, résident entre les adresses données par les opérandes.

## <a name="see-also"></a>Voir aussi

[Opérateurs additifs C](../c-language/c-additive-operators.md)