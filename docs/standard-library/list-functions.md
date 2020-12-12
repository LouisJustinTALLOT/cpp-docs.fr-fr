---
description: 'En savoir plus sur : les &lt; fonctions de liste &gt;'
title: '&lt;répertorier les &gt; fonctions | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- list/std::swap
ms.openlocfilehash: 6a94fcc916db08a510a968b66b0a0dc0cfa9b8e5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97284705"
---
# <a name="ltlistgt-functions"></a>&lt;répertorier les &gt; fonctions

## <a name="swap"></a><a name="swap"></a> échange

Échange les éléments de deux listes.

```cpp
template <class T, class Allocator>
    void swap(list<T, Allocator>& left, list<T, Allocator>& right)
```

### <a name="parameters"></a>Paramètres

*gauche*\
Objet de type `list`.

*Oui*\
Objet de type `list`.

### <a name="remarks"></a>Notes

La fonction de modèle exécute `left.swap(right)`.
