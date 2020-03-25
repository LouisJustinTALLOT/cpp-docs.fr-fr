---
title: Avertissement du compilateur (niveau 1) C4109
ms.date: 11/04/2016
f1_keywords:
- C4109
helpviewer_keywords:
- C4109
ms.assetid: 9e8d95c6-e05d-47e0-bd87-78974b3cc06c
ms.openlocfilehash: 04252f6100f0cabcd6bca0ff4145b55cfcadd234
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200120"
---
# <a name="compiler-warning-level-1-c4109"></a>Avertissement du compilateur (niveau 1) C4109

Identificateur 'identifier' inattendu

Le pragma contenant l’identificateur inattendu est ignoré.

## <a name="example"></a>Exemple

```cpp
// C4109.cpp
// compile with: /W1 /LD
#pragma init_seg( abc ) // C4109
```
