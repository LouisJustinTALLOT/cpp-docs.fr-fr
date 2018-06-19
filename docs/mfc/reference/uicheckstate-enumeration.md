---
title: Énumération UICheckState | Documents Microsoft
ms.custom: ''
ms.date: 04/03/2017
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- afxwinforms/uicheckstate
dev_langs:
- C++
helpviewer_keywords:
- uicheckstate enumeration [MFC]
ms.assetid: 2ac0098c-20e7-410c-9685-5ead5cb02b63
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 11c326de6b30668265ff57de73021bcd526baa5c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33375420"
---
# <a name="uicheckstate-enumeration"></a>Énumération UICheckState
Décrit l’état d’activation d’un élément d’interface utilisateur pour la commande.  
   
### <a name="syntax"></a>Syntaxe   
```  
public enum class 
{  
   [DefaultValue(typeid<Microsoft::VisualC::MFC::UICheckState>, "Checked")]  
   Unchecked,   
   Checked,   
   Indeterminate 
};  
```  
   
### <a name="remarks"></a>Notes  
 [ICommandUI::Check](icommandui-interface.md#check) utilise ces valeurs pour décrire l’état d’un élément d’interface utilisateur.    
 Pour plus d’informations sur l’utilisation de Windows Forms, consultez [à l’aide d’un contrôle d’utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
   
### <a name="requirements"></a>Spécifications  
 **En-tête :** afxwinforms.h (défini dans l’assembly atlmfc\lib\mfcmifc80.dll)  
