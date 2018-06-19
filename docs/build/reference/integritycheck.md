---
title: /INTEGRITYCHECK | Documents Microsoft
ms.custom: ''
ms.date: 12/28/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /INTEGRITYCHECK
dev_langs:
- C++
helpviewer_keywords:
- -INTEGRITYCHECK editbin options
- /INTEGRITYCHECK editbin options
- INTEGRITYCHECK editbin options
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b0adf9add2d191ae89aec0a5d756ade8e9f7725
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32370246"
---
# <a name="integritycheck"></a>/INTEGRITYCHECK

Spécifie que la signature numérique de l’image binaire doit être vérifiée au moment du chargement.

> **/INTEGRITYCHECK**[**: NO**]

## <a name="remarks"></a>Notes

Dans l’en-tête du fichier DLL ou du fichier exécutable, cette option définit un indicateur qui requiert une vérification de signature numérique par le Gestionnaire de mémoire pour charger l’image de Windows. Les versions de Windows antérieures à Windows Vista ignorent cet indicateur. Cette option doit être définie pour les dll 64 bits qui implémentent de code en mode noyau et sont recommandées pour tous les pilotes de périphérique. Pour plus d’informations, consultez [spécifications de signature de Code en Mode noyau](/windows-hardware/drivers/install/kernel-mode-code-signing-requirements--windows-vista-and-later-).

## <a name="see-also"></a>Voir aussi

[Options EDITBIN](../../build/reference/editbin-options.md)  
