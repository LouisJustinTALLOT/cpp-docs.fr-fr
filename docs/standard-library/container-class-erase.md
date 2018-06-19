---
title: Conteneur Class::erase | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- erase method
ms.assetid: abc091c5-5a80-4bd8-93a8-a2d9bde2efec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 368b722f03a68445ddd016705aa8bebc6f33e6f5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33842610"
---
# <a name="container-classerase"></a>Conteneur Class::erase

> [!NOTE]
> Cette rubrique fait partie de la documentation Visual C++ comme exemple non fonctionnel de conteneurs utilisés dans la bibliothèque standard C++. Pour plus d’informations, consultez [Conteneurs de la bibliothèque standard C++](../standard-library/stl-containers.md).

Efface un élément.

## <a name="syntax"></a>Syntaxe

```

    iterator erase(
    iterator _Where);

iterator erase(
    iterator first,
    iterator last);
```

## <a name="remarks"></a>Notes

La première fonction membre supprime l’élément de la séquence contrôlée vers lequel pointé *_Where*. La deuxième fonction membre supprime l’élément de la séquence contrôlée dans la plage [`first`, `last`). Les deux fonctions retournent un itérateur qui désigne le premier élément restant après tous les éléments supprimés, ou [end](../standard-library/container-class-end.md) si aucun élément de ce genre n’existe.

Les fonctions membres lèvent une exception uniquement si une opération de copie lève une exception.

## <a name="see-also"></a>Voir aussi

[Sample Container, classe](../standard-library/sample-container-class.md)<br/>
