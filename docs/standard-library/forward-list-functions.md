---
description: 'En savoir plus sur les fonctions suivantes : &lt; forward_list &gt;'
title: '&lt;forward_list&gt;, fonctions'
ms.date: 11/04/2016
f1_keywords:
- forward_list/std::swap
ms.assetid: 0d6bc656-7049-4651-a4bd-c9a805e47756
ms.openlocfilehash: 3f827b777f2e6fa62dd78c7d737d5da84b50610c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324350"
---
# <a name="ltforward_listgt-functions"></a>&lt;forward_list&gt;, fonctions

## <a name="swap"></a><a name="swap"></a> échange

Échange les éléments de deux forward_list.

```cpp
void swap(forward_list <Type, Allocator>& left, forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `forward_list`.

*Oui*\
Objet de type `forward_list`.

### <a name="remarks"></a>Notes

La fonction de modèle exécute `left.swap(right)`.
