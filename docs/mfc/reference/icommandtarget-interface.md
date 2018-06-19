---
title: Interface de ICommandTarget | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- ICommandTarget
- AFXWINFORMS/ICommandTarget
- AFXWINFORMS/ICommandTarget::Initialize
dev_langs:
- C++
helpviewer_keywords:
- ICommandTarget interface [MFC]
ms.assetid: dd9927f6-3479-4e7c-8ef9-13206cf901f3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b32112fbad516b2550da0cc48cb6c287583d396c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33375575"
---
# <a name="icommandtarget-interface"></a>Interface de ICommandTarget
Fournit un contrôle utilisateur avec une interface pour recevoir des commandes à partir d’un objet de source de commande.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
interface class ICommandTarget  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[ICommandTarget::Initialize](#initialize)|Initialise l’objet cible de commande.|  
  
## <a name="remarks"></a>Notes  
 Lorsque vous hébergez un contrôle utilisateur dans une vue de MFC, [CWinFormsView](../../mfc/reference/cwinformsview-class.md) commandes d’itinéraires et mise à jour de commande des messages de l’interface utilisateur pour le contrôle utilisateur pour lui permettre de gérer les commandes MFC (par exemple, les éléments de menu de frame et boutons de barre d’outils). En implémentant `ICommandTarget`, vous donnez le contrôle utilisateur, une référence à la [ICommandSource](../../mfc/reference/icommandsource-interface.md) objet.  
  
 Consultez [Comment : ajouter routage des commandes pour le contrôle Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) pour obtenir un exemple montrant comment utiliser `ICommandTarget`.  
  
 Pour plus d’informations sur l’utilisation de Windows Forms, consultez [à l’aide d’un contrôle d’utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxwinforms.h (défini dans l’assembly atlmfc\lib\mfcmifc80.dll)  
  
##  <a name="initialize"></a> ICommandTarget::Initialize  
 Initialise l’objet cible de commande.  
  
```  
void Initialize(ICommandSource^ cmdSource);  
```  
  
### <a name="parameters"></a>Paramètres  
 `cmdSource`  
 Handle vers l’objet de source de commande.  
  
### <a name="remarks"></a>Notes  
 Lorsque vous hébergez un contrôle utilisateur dans une vue de MFC, CWinFormsView achemine les commandes et les messages de l’interface utilisateur de commande de mise à jour pour le contrôle utilisateur pour lui permettre de gérer les commandes MFC.  
  
 Cette méthode initialise l’objet cible de commande et l’associe le cmdSource d’objet de source de commande spécifiée. Elle doit être appelée dans l’implémentation de classe du contrôle utilisateur. Lors de l’initialisation, vous devez inscrire les gestionnaires de commandes avec l’objet de source de commande en appelant ICommandSource::AddCommandHandler dans l’implémentation de l’initialisation. Consultez Comment : ajouter le routage des commandes au contrôle Windows Forms pour obtenir un exemple d’utilisation d’initialisation pour ce faire.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : ajouter des commandes routage pour le Windows Forms contrôle](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)   
 [ICommandSource, interface](../../mfc/reference/icommandsource-interface.md)



