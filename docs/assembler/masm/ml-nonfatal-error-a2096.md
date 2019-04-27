---
title: Erreur ML non fatale A2096
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A2096
helpviewer_keywords:
- A2096
ms.assetid: bab0b5ee-b39f-4e44-a41a-3f949fab4297
ms.openlocfilehash: e6b31afeff801e7128b5a76576e9eaa3398f68e5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62202488"
---
# <a name="ml-nonfatal-error-a2096"></a>Erreur ML non fatale A2096

**segment, groupe ou un Registre de segment attendu**

Un segment ou un groupe était attendu mais n’a été trouvé.

Parmi les options suivantes s’est produite :

- L’opérande gauche est spécifié avec le segment de substituer l’opérateur (**:**) n’était pas un segment register (CS, DS, SS, ES, FS ou GS), nom du groupe, nom de segment ou expression de segment.

- Le [ASSUME](../../assembler/masm/assume.md) directive ont été fournie à un Registre de segment sans une adresse valide de segment, Registre de segment, groupe ou spéciale **plat** groupe.

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)<br/>