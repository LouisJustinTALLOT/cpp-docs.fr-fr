---
title: copyin | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- copyin
dev_langs:
- C++
helpviewer_keywords:
- copyin OpenMP clause
ms.assetid: 369efa88-613c-4cb1-9e11-7b9ee08a4b25
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 424bb8eaa41e3bbb0cf697df108adcef116e1b04
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46379578"
---
# <a name="copyin"></a>copyin

Permet aux threads d’accéder à valeur du thread principal, pour un [threadprivate](../../../parallel/openmp/reference/threadprivate.md) variable.

## <a name="syntax"></a>Syntaxe

```
copyin(var)
```

## <a name="parameters"></a>Paramètres

*var*<br/>
Le `threadprivate` variable qui sera initialisé avec la valeur de la variable dans le thread principal, tel qu’il existe avant la construction parallèle.

## <a name="remarks"></a>Notes

`copyin` s’applique aux directives suivantes :

- [parallel](../../../parallel/openmp/reference/parallel.md)

- [for](../../../parallel/openmp/reference/for-openmp.md)

- [sections](../../../parallel/openmp/reference/sections-openmp.md)

Pour plus d’informations, consultez [2.7.2.7 copyin](../../../parallel/openmp/2-7-2-7-copyin.md).

## <a name="example"></a>Exemple

Consultez [threadprivate](../../../parallel/openmp/reference/threadprivate.md) pour obtenir un exemple d’utilisation de `copyin`.

## <a name="see-also"></a>Voir aussi

[Clauses](../../../parallel/openmp/reference/openmp-clauses.md)