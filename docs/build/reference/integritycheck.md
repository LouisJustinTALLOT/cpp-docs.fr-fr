---
title: /INTEGRITYCHECK
ms.date: 12/28/2017
f1_keywords:
- /INTEGRITYCHECK
helpviewer_keywords:
- -INTEGRITYCHECK editbin options
- /INTEGRITYCHECK editbin options
- INTEGRITYCHECK editbin options
ms.openlocfilehash: 4174e22dcdadb3b3319998614285c13741fe3a88
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269763"
---
# <a name="integritycheck"></a>/INTEGRITYCHECK

Spécifie que la signature numérique de l’image binaire doit être vérifiée au moment du chargement.

> **/INTEGRITYCHECK**[**:NO**]

## <a name="remarks"></a>Notes

Dans l’en-tête du fichier DLL ou du fichier exécutable, cette option définit un indicateur qui requiert une vérification de signature numérique par le Gestionnaire de mémoire pour charger l’image dans Windows. Les versions de Windows antérieures à Windows Vista ignorent cet indicateur. Cette option doit être définie pour les dll 64 bits qui implémentent le code en mode noyau et sont recommandées pour tous les pilotes de périphérique. Pour plus d’informations, consultez [exigences de signature de Code en Mode noyau](/windows-hardware/drivers/install/kernel-mode-code-signing-requirements--windows-vista-and-later-).

## <a name="see-also"></a>Voir aussi

[Options EDITBIN](editbin-options.md)
