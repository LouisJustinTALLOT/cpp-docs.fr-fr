---
description: 'En savoir plus sur : énumération UICheckState'
title: Énumération UICheckState
ms.date: 04/03/2017
f1_keywords:
- afxwinforms/uicheckstate
helpviewer_keywords:
- uicheckstate enumeration [MFC]
ms.assetid: 2ac0098c-20e7-410c-9685-5ead5cb02b63
ms.openlocfilehash: 8c6f250dd6f6646d22aac0fa819b73537ee0f443
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218639"
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

[ICommandUI :: Check](icommandui-interface.md#check) utilise ces valeurs pour décrire l’état d’un élément d’interface utilisateur.
Pour plus d’informations sur l’utilisation de Windows Forms, consultez [utilisation d’un contrôle utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Spécifications

**En-tête :** afxwinforms. h (défini dans l’assembly atlmfc\lib\mfcmifc80.dll)
