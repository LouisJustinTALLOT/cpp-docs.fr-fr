---
title: alloca
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 2b209335-e3a0-4934-93f0-3b5925d22918
ms.openlocfilehash: 2c528a9cdecc52afa1e7d59f58160b247cecfee2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491622"
---
# <a name="alloca"></a>alloca

[_alloca](../c-runtime-library/reference/alloca.md) doit être de 16 octets alignée et utiliser un pointeur de frame.

La pile est allouée doit inclure l’espace en dessous pour les paramètres des fonctions appelées par la suite, comme indiqué dans [Allocation de piles](../build/stack-allocation.md).

## <a name="see-also"></a>Voir aussi

[Utilisation de la pile](../build/stack-usage.md)