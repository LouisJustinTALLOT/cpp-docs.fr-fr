---
title: DEVNAMES, Structure | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- DEVNAMES
dev_langs:
- C++
helpviewer_keywords:
- DEVNAMES [MFC]
ms.assetid: aac97f60-2169-471a-ba5d-c0baed9eed9a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d91a44a38d331a49927d5129c5002eef53c224ad
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50077970"
---
# <a name="devnames-structure"></a>DEVNAMES, structure

Le `DEVNAMES` structure contient des chaînes qui identifient le pilote, appareil et les noms de port de sortie pour une imprimante.

## <a name="syntax"></a>Syntaxe

```
typedef struct tagDEVNAMES { /* dvnm */
    WORD wDriverOffset;
    WORD wDeviceOffset;
    WORD wOutputOffset;
    WORD wDefault; */* driver,
    device,
    and port-name strings follow wDefault */
} DEVNAMES;
```

#### <a name="parameters"></a>Paramètres

*wDriverOffset*<br/>
(Entrée/sortie) Spécifie le décalage en caractères en une chaîne se terminant par null qui contient le nom de fichier (sans l’extension) du pilote de périphérique. En entrée, cette chaîne est utilisée pour déterminer l’imprimante à afficher initialement dans la boîte de dialogue.

*wDeviceOffset*<br/>
(Entrée/sortie) Spécifie le décalage de caractères à la chaîne se terminant par null (maximum de 32 octets, y compris la valeur null) qui contient le nom de l’appareil. Cette chaîne doit être identique à la `dmDeviceName` membre de la [DEVMODE](/windows/desktop/api/wingdi/ns-wingdi-_devicemodea) structure.

*wOutputOffset*<br/>
(Entrée/sortie) Spécifie le décalage de caractères à la chaîne se terminant par null qui contient le nom de périphérique DOS pour la sortie physique du port de sortie.

*wDefault*<br/>
Spécifie si les chaînes contenues dans le `DEVNAMES` structure identifier l’imprimante par défaut. Cette chaîne est utilisée pour vérifier que l’imprimante par défaut n’a pas changé depuis la dernière opération d’impression. En entrée, si l’indicateur DN_DEFAULTPRN est défini, l’autre les valeurs dans le `DEVNAMES` structure sont vérifiées par rapport à l’imprimante par défaut actuel. Si aucune de ces chaînes ne correspondent pas, un message d’avertissement s’affiche pour informer l’utilisateur que le document peut devoir être reformaté. Lors de la sortie, le `wDefault` membre est modifié uniquement si la boîte de dialogue de configuration de l’impression a été affichée et l’utilisateur a choisi le bouton OK. L’indicateur DN_DEFAULTPRN est défini si l’imprimante par défaut a été sélectionné. Si une imprimante spécifique est sélectionnée, l’indicateur n’est pas défini. Tous les autres bits dans ce membre sont réservés à un usage interne par la procédure de boîte de dialogue d’impression.

## <a name="remarks"></a>Notes

Le `PrintDlg` fonction utilise ces chaînes pour initialiser les membres dans la boîte de dialogue Imprimer définie par le système. Lorsque l’utilisateur ferme la boîte de dialogue, les informations sur l’imprimante sélectionnée sont retournées dans cette structure.

## <a name="requirements"></a>Configuration requise

**En-tête :** commdlg.h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CPrintDialog::CreatePrinterDC](../../mfc/reference/cprintdialog-class.md#createprinterdc)

