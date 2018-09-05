---
title: ML erreur non fatale A2008 | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2008
dev_langs:
- C++
helpviewer_keywords:
- A2008
ms.assetid: ca24157f-c88a-4678-ae06-3bc3cd956001
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 774cf4c2a51bf084fb63e572cc99b0c8e3cba26f
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43679373"
---
# <a name="ml-nonfatal-error-a2008"></a>Erreur ML non fatale A2008

**Erreur de syntaxe :**

Un jeton à l’emplacement actuel a provoqué une erreur de syntaxe.

Parmi les options suivantes peut-être se sont produites :

- Un préfixe de point a été ajouté à ou omis à partir d’une directive.

- Un mot réservé (tel que **C** ou **taille**) a été utilisé en tant qu’identificateur.

- Une instruction a été utilisée qui n’était pas disponible avec la sélection actuelle du processeur ou de coprocesseur.

- Un opérateur d’exécution de comparaison (tels que `==`) a été utilisé dans une instruction conditionnelle assembly au lieu d’un opérateur relationnel (tel que [EQ](../../assembler/masm/operator-eq.md)).

- Une instruction ou la directive a été donnée trop peu d’opérandes.

- Une directive obsolète a été utilisée.

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)<br/>