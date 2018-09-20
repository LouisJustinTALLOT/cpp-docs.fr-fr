---
title: lastprivate | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- lastprivate
dev_langs:
- C++
helpviewer_keywords:
- lastprivate OpenMP clause
ms.assetid: 6ef87b31-375a-47e8-8d0d-281be45fb56a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7124e51b604a55d049be13d3bbcccc4e5810ca67
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412832"
---
# <a name="lastprivate"></a>lastprivate

Spécifie que la version du contexte englobant de la variable est définie égale à la version privée du thread quelconque qui exécute la dernière itération (construction de boucle for) ou la dernière section (sections #pragma).

## <a name="syntax"></a>Syntaxe

```
lastprivate(var)
```

### <a name="parameters"></a>Paramètres

*var*<br/>
La variable est égale à la version privée du thread quelconque qui exécute la dernière itération (construction de boucle for) ou la dernière section (sections #pragma).

## <a name="remarks"></a>Notes

`lastprivate` s’applique aux directives suivantes :

- [for](../../../parallel/openmp/reference/for-openmp.md)

- [sections](../../../parallel/openmp/reference/sections-openmp.md)

Pour plus d’informations, consultez [2.7.2.3 lastprivate](../../../parallel/openmp/2-7-2-3-lastprivate.md).

## <a name="example"></a>Exemple

Consultez [planification](../../../parallel/openmp/reference/schedule.md) pour obtenir un exemple d’utilisation `lastprivate` clause.

## <a name="see-also"></a>Voir aussi

[Clauses](../../../parallel/openmp/reference/openmp-clauses.md)