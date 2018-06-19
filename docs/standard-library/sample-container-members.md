---
title: sample container, membres | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- container classes
ms.assetid: dc5a1998-a31b-4adf-b888-8abe5b87a4e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7c844416151874714aa86a2ffe9762949c6a62a3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33856096"
---
# <a name="sample-container-members"></a>sample container, membres

> [!NOTE]
> Cette rubrique fait partie de la documentation Visual C++ comme exemple non fonctionnel de conteneurs utilisés dans la bibliothèque standard C++. Pour plus d’informations, consultez [Conteneurs de la bibliothèque standard C++](../standard-library/stl-containers.md).

## <a name="reference"></a>Référence

## <a name="typedefs"></a>Typedef

|||
|-|-|
|[const_iterator](../standard-library/container-class-const-iterator.md)|Décrit un objet pouvant servir d’itérateur constant pour la séquence contrôlée.|
|[const_reference](../standard-library/container-class-const-reference.md)|Décrit un objet pouvant servir de référence constante à un élément de la séquence contrôlée.|
|[const_reverse_iterator](../standard-library/container-class-const-reverse-iterator.md)|Décrit un objet pouvant servir d’itérateur inverse constant pour la séquence contrôlée.|
|[difference_type](../standard-library/container-class-difference-type.md)|Décrit un objet qui peut représenter la différence entre les adresses de deux éléments quelconques dans la séquence contrôlée.|
|[iterator](../standard-library/container-class-iterator.md)|Décrit un objet pouvant servir d’itérateur pour la séquence contrôlée.|
|[reference](../standard-library/container-class-reference.md)|Décrit un objet pouvant servir de référence à un élément de la séquence contrôlée.|
|[reverse_iterator](../standard-library/container-class-reverse-iterator.md)|Décrit un objet pouvant servir d’itérateur inverse pour la séquence contrôlée.|
|[size_type](../standard-library/container-class-size-type.md)|Décrit un objet qui peut représenter la longueur de n’importe quelle séquence contrôlée.|
|[value_type](../standard-library/container-class-value-type.md)|Est un synonyme du paramètre de modèle **Ty**.|

## <a name="member-functions"></a>Fonctions membres

|||
|-|-|
|[begin](../standard-library/container-class-begin.md)|Retourne un itérateur qui pointe vers le premier élément de la séquence (ou juste après la fin d’une séquence vide).|
|[clear](../standard-library/container-class-clear.md)|Appelle [erase](../standard-library/container-class-erase.md)( [begin](../standard-library/container-class-begin.md), [end](../standard-library/container-class-end.md)).|
|[empty](../standard-library/container-class-empty.md)|Retourne la valeur **true** pour une séquence contrôlée vide.|
|[end](../standard-library/container-class-end.md)|Retourne un itérateur qui pointe juste après la fin de la séquence.|
|[erase](../standard-library/container-class-erase.md)|Efface un élément.|
|[max_size](../standard-library/container-class-max-size.md)|Retourne la longueur de la séquence la plus longue que l’objet peut contrôler, en temps constant, quelle que soit la longueur de la séquence contrôlée.|
|[rbegin](../standard-library/container-class-rbegin.md)|Retourne un itérateur inverse qui pointe juste après la fin de la séquence contrôlée, désignant ainsi le début de la séquence inverse.|
|[rend](../standard-library/container-class-rend.md)|La fonction membre retourne un itérateur inverse qui pointe vers le premier élément de la séquence (ou juste après la fin d’une séquence vide), désignant ainsi la fin de la séquence inverse.|
|[size](../standard-library/container-class-size.md)|Retourne la longueur de la séquence contrôlée en temps constant, quelle qu’elle soit.|
|[swap](../standard-library/container-class-swap.md)
