---
title: ML erreur non fatale A2096 | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2096
dev_langs:
- C++
helpviewer_keywords:
- A2096
ms.assetid: bab0b5ee-b39f-4e44-a41a-3f949fab4297
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 82f4ef76dca10b1208a931bc3e1cc09d82a639d2
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43679596"
---
# <a name="ml-nonfatal-error-a2096"></a>Erreur ML non fatale A2096

**segment, groupe ou un Registre de segment attendu**

Un segment ou un groupe était attendu mais n’a été trouvé.

Parmi les options suivantes s’est produite :

- L’opérande gauche est spécifié avec le segment de substituer l’opérateur (**:**) n’était pas un segment register (CS, DS, SS, ES, FS ou GS), nom du groupe, nom de segment ou expression de segment.

- Le [ASSUME](../../assembler/masm/assume.md) directive ont été fournie à un Registre de segment sans une adresse valide de segment, Registre de segment, groupe ou spéciale **plat** groupe.

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)<br/>