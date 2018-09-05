---
title: ML erreur non fatale A2066 | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2066
dev_langs:
- C++
helpviewer_keywords:
- A2066
ms.assetid: 58220fdf-fb8f-47fc-a36d-737867361185
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8cf5cbe7d5c77da7f129cbc40ffa97f4051afca6
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43690250"
---
# <a name="ml-nonfatal-error-a2066"></a>Erreur ML non fatale A2066

**incompatible taille mode et le même segment de processeur**

Une tentative a été effectuée pour ouvrir un segment avec un **USE16**, **USE32**, ou **plat** attribut qui n’était pas compatible avec le processeur spécifié, ou pour modifier un processeur de 16 bits en 32 bits segment.

Le **USE32** et **plat** attributs doivent être précédés par le.386 ou directive de processeur supérieure.

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)<br/>