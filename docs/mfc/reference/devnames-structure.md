---
title: DEVNAMES, Structure | Documents Microsoft
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
ms.openlocfilehash: 0c13167c42c6acbfcc5f3af500205eed6ab884d9
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37121573"
---
# <a name="devnames-structure"></a>DEVNAMES, structure
Le `DEVNAMES` structure contient des chaînes qui identifient le pilote, appareil et les noms de port de sortie d’une imprimante.  
  
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
 *wDriverOffset*  
 (Entrée/sortie) Spécifie le décalage de caractères en une chaîne terminée par le caractère null qui contient le nom de fichier (sans l’extension) du pilote de périphérique. En entrée, cette chaîne est utilisée pour déterminer l’imprimante à afficher initialement dans la boîte de dialogue.  
  
 *wDeviceOffset*  
 (Entrée/sortie) Spécifie le décalage de caractères à la chaîne se terminant par null (maximum de 32 octets, y compris la valeur null) qui contient le nom de l’appareil. Cette chaîne doit être identique à la `dmDeviceName` membre de la [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) structure.  
  
 *wOutputOffset*  
 (Entrée/sortie) Spécifie le décalage de caractères à la chaîne se terminant par null qui contient le nom de périphérique DOS pour la sortie physique du port de sortie.  
  
 *wDefault*  
 Spécifie si les chaînes contenues dans le `DEVNAMES` structure identifier l’imprimante par défaut. Cette chaîne est utilisée pour vérifier que l’imprimante par défaut n’a pas changé depuis la dernière opération d’impression. En entrée, si l’indicateur DN_DEFAULTPRN est défini, les autres valeurs dans le `DEVNAMES` structure sont vérifiées par rapport à l’imprimante par défaut en cours. Si aucune de ces chaînes ne correspondent pas, un message d’avertissement s’affiche pour informer l’utilisateur qui doivent être remises en forme le document. En sortie, le `wDefault` membre est modifié uniquement si la boîte de dialogue Configuration de l’impression est affichée et l’utilisateur a choisi le bouton OK. L’indicateur DN_DEFAULTPRN est défini si l’imprimante par défaut a été sélectionnée. Si une imprimante spécifique est sélectionnée, l’indicateur n’est pas défini. Tous les autres bits dans ce membre sont réservés à un usage interne par la procédure de boîte de dialogue d’impression.  
  
## <a name="remarks"></a>Notes  
 Le `PrintDlg` fonction utilise ces chaînes pour initialiser les membres dans la boîte de dialogue Imprimer définies par le système. Lorsque l’utilisateur ferme la boîte de dialogue, les informations sur l’imprimante sélectionnée sont retournées dans cette structure.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** commdlg.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CPrintDialog::CreatePrinterDC](../../mfc/reference/cprintdialog-class.md#createprinterdc)


