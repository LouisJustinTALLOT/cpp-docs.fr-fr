---
title: Énumération UICheckState
ms.date: 04/03/2017
f1_keywords:
- afxwinforms/uicheckstate
helpviewer_keywords:
- uicheckstate enumeration [MFC]
ms.assetid: 2ac0098c-20e7-410c-9685-5ead5cb02b63
ms.openlocfilehash: 6e04015f33012ddd1c0a75187c89eadedbe01e3d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528139"
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

### <a name="requirements"></a>Configuration requise

**En-tête :** afxwinforms.h (défini dans l’assembly atlmfc\lib\mfcmifc80.dll)
