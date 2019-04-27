---
title: Erreur ML irrécupérable A1007
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A1007
helpviewer_keywords:
- A1007
ms.assetid: bcf9c826-beb3-4e93-91fe-1ffd34995fbf
ms.openlocfilehash: 98933c3a24da22f447174a3b51c4855690aba83e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62177901"
---
# <a name="ml-fatal-error-a1007"></a>Erreur ML irrécupérable A1007

**niveau d’imbrication trop profond**

L’assembleur atteint sa limite d’imbrication. La limite est de 20 niveaux sauf indication contraire.

Parmi les options suivantes a été imbriqué trop profondément :

- Une directive de haut niveau tels que [. IF](../../assembler/masm/dot-if.md), [. RÉPÉTEZ](../../assembler/masm/dot-repeat.md), ou [. Bien que](../../assembler/masm/dot-while.md).

- Une définition de structure.

- Une directive conditionnelle de l’assembly.

- Une définition de procédure.

- Un [PUSHCONTEXT](../../assembler/masm/pushcontext.md) directive (la limite est 10).

- Une définition des segments.

- Un fichier include.

- Une macro.

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)<br/>