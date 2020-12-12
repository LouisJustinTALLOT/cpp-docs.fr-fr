---
description: En savoir plus sur:/INTEGRITYCHECK
title: /INTEGRITYCHECK
ms.date: 12/28/2017
f1_keywords:
- /INTEGRITYCHECK
helpviewer_keywords:
- -INTEGRITYCHECK editbin options
- /INTEGRITYCHECK editbin options
- INTEGRITYCHECK editbin options
ms.openlocfilehash: b1ea8275bdb356febcf18a2a55b6ab718d8eea96
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199660"
---
# <a name="integritycheck"></a>/INTEGRITYCHECK

Spécifie que la signature numérique de l’image binaire doit être vérifiée au moment du chargement.

> **/INTEGRITYCHECK**[**: no**]

## <a name="remarks"></a>Notes

Dans l’en-tête du fichier DLL ou du fichier exécutable, cette option définit un indicateur qui requiert une vérification de signature numérique par le gestionnaire de mémoire pour charger l’image dans Windows. Les versions de Windows antérieures à Windows Vista ignorent cet indicateur. Cette option doit être définie pour les dll 64 bits qui implémentent le code en mode noyau et est recommandée pour tous les pilotes de périphérique. Pour plus d’informations, consultez [Configuration requise pour la signature de code en mode noyau](/windows-hardware/drivers/install/kernel-mode-code-signing-requirements--windows-vista-and-later-).

## <a name="see-also"></a>Voir aussi

[Options EDITBIN](editbin-options.md)
