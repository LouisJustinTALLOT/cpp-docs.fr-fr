---
title: Erreur RC2151 du compilateur de ressources
ms.date: 11/04/2016
f1_keywords:
- RC2151
helpviewer_keywords:
- RC2151
ms.assetid: 3c47e535-c78d-4338-aab9-9b47e2c34728
ms.openlocfilehash: 9d4eea92321ca8373f3ad5f121f4a8e96d878e79
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191260"
---
# <a name="resource-compiler-error-rc2151"></a>Erreur RC2151 du compilateur de ressources

Impossible de réutiliser les constantes de chaîne

Vous utilisez la même valeur deux fois dans une instruction **STRINGTABLE** . Assurez-vous que vous ne mélangez pas les valeurs décimales et hexadécimales qui se chevauchent.

Chaque ID dans une **STRINGTABLE** doit être unique. Pour une efficacité maximale, utilisez des constantes contiguës qui démarrent sur un multiple de 16.
