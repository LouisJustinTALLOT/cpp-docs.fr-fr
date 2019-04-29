---
title: Énumération UICheckState
ms.date: 04/03/2017
f1_keywords:
- afxwinforms/uicheckstate
helpviewer_keywords:
- uicheckstate enumeration [MFC]
ms.assetid: 2ac0098c-20e7-410c-9685-5ead5cb02b63
ms.openlocfilehash: 1411e9b7cb088c063e17cc7c59871e5f0b83ad9c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62309796"
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
