---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4109'
title: Avertissement du compilateur (niveau 1) C4109
ms.date: 11/04/2016
f1_keywords:
- C4109
helpviewer_keywords:
- C4109
ms.assetid: 9e8d95c6-e05d-47e0-bd87-78974b3cc06c
ms.openlocfilehash: 2063b6d9f85e497892bad27bc1b553872a309b17
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97267506"
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
