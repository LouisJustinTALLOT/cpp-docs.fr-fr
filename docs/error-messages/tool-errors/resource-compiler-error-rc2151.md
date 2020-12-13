---
description: 'En savoir plus sur : erreur du compilateur de ressources RC2151'
title: 'Erreur RC2151 du compilateur de ressources '
ms.date: 11/04/2016
f1_keywords:
- RC2151
helpviewer_keywords:
- RC2151
ms.assetid: 3c47e535-c78d-4338-aab9-9b47e2c34728
ms.openlocfilehash: 0a5056291d682d91c7b7feb3de4556473d9a833d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97133404"
---
# <a name="resource-compiler-error-rc2151"></a>Erreur RC2151 du compilateur de ressources 

Impossible de réutiliser les constantes de chaîne

Vous utilisez la même valeur deux fois dans une instruction **STRINGTABLE** . Assurez-vous que vous ne mélangez pas les valeurs décimales et hexadécimales qui se chevauchent.

Chaque ID dans une **STRINGTABLE** doit être unique. Pour une efficacité maximale, utilisez des constantes contiguës qui démarrent sur un multiple de 16.
