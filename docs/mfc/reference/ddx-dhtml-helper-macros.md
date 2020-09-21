---
title: Macros d’assistance DDX_DHtml
ms.date: 11/04/2016
f1_keywords:
- AFXDHTML/DDX_DHtml_ElementValue
- AFXDHTML/DDX_DHtml_ElementInnerText
- AFXDHTML/DDX_DHtml_ElementInnerHtml
- AFXDHTML/DDX_DHtml_Anchor_Href
- AFXDHTML/DDX_DHtml_Anchor_Target
- AFXDHTML/DDX_DHtml_Img_Src
- AFXDHTML/DDX_DHtml_Frame_Src
- AFXDHTML/DDX_DHtml_IFrame_Src
helpviewer_keywords:
- macros [MFC], exchanging data with HMTL pages
- DDX macros [MFC]
- HTML pages [MFC], helper macros
- DDX (dialog data exchange), DHtml helper macros
- macros [MFC], DDX_DHtml helpers
ms.assetid: c46302d2-ea43-4fea-bfc2-6f590d99f267
ms.openlocfilehash: eeea85872422edcf421ba2fe254c8f03c093fe3c
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743449"
---
# <a name="ddx_dhtml-helper-macros"></a>Macros d’assistance DDX_DHtml

Les macros d’assistance DDX_DHtml permettent d’accéder facilement aux propriétés couramment utilisées des contrôles sur une page HTML.

### <a name="data-exchange-macros"></a>Macros d’échange de données

|Nom|Description|
|-|-|
|[DDX_DHtml_ElementValue](#ddx_dhtml_elementvalue)|Définit ou récupère la propriété de valeur à partir du contrôle sélectionné.|
|[DDX_DHtml_ElementInnerText](#ddx_dhtml_elementinnertext)|Définit ou récupère le texte entre les balises de début et de fin de l’élément actuel.|
|[DDX_DHtml_ElementInnerHtml](#ddx_dhtml_elementinnerhtml)|Définit ou récupère le code HTML entre les balises de début et de fin de l’élément actuel.|
|[DDX_DHtml_Anchor_Href](#ddx_dhtml_anchor_href)|Définit ou récupère l’URL de destination ou le point d’ancrage.|
|[DDX_DHtml_Anchor_Target](#ddx_dhtml_anchor_target)|Définit ou récupère la fenêtre ou le frame cible.|
|[DDX_DHtml_Img_Src](#ddx_dhtml_img_src)|Définit ou récupère le nom d’une image ou d’un clip vidéo dans le document.|
|[DDX_DHtml_Frame_Src](#ddx_dhtml_frame_src)|Définit ou récupère l’URL du frame associé.|
|[DDX_DHtml_IFrame_Src](#ddx_dhtml_iframe_src)|Définit ou récupère l’URL du frame associé.|

## <a name="requirements"></a>Spécifications

**En-tête :** afxdhtml. h

## <a name="ddx_dhtml_anchor_href"></a><a name="ddx_dhtml_anchor_href"></a> DDX_DHtml_Anchor_Href

Définit ou récupère l’URL de destination ou le point d’ancrage.

```
DDX_DHtml_Anchor_Href(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Paramètres

*DX*<br/>
Pointeur vers un objet [CDataExchange](../../mfc/reference/cdataexchange-class.md) .

*name*<br/>
Valeur que vous avez spécifiée pour le paramètre ID du contrôle HTML.

*var*<br/>
Valeur en cours d’échange.

### <a name="remarks"></a>Notes

Cette macro appelle la fonction [CDHtmlDialog ::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) à l’aide de l’ID de distribution DISPID_IHTMLANCHORELEMENT_HREF.

## <a name="ddx_dhtml_anchor_target"></a><a name="ddx_dhtml_anchor_target"></a> DDX_DHtml_Anchor_Target

Définit ou récupère la fenêtre ou le frame cible.

```
DDX_DHtml_Anchor_Target(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Paramètres

*DX*<br/>
Pointeur vers un objet [CDataExchange](../../mfc/reference/cdataexchange-class.md) .

*name*<br/>
Valeur que vous avez spécifiée pour le paramètre ID du contrôle HTML.

*var*<br/>
Valeur en cours d’échange.

### <a name="remarks"></a>Notes

Cette macro appelle la fonction [CDHtmlDialog ::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) à l’aide de l’ID de distribution DISPID_IHTMLANCHORELEMENT_TARGET.

## <a name="ddx_dhtml_elementinnerhtml"></a><a name="ddx_dhtml_elementinnerhtml"></a> DDX_DHtml_ElementInnerHtml

Définit ou récupère le code HTML entre les balises de début et de fin de l’élément actuel.

```
DDX_DHtml_ElementInnerHtml(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Paramètres

*DX*<br/>
Pointeur vers un objet [CDataExchange](../../mfc/reference/cdataexchange-class.md) .

*name*<br/>
Valeur que vous avez spécifiée pour le paramètre ID du contrôle HTML.

*var*<br/>
Valeur en cours d’échange.

### <a name="remarks"></a>Notes

Cette macro appelle la fonction [CDHtmlDialog ::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) à l’aide de l’ID de distribution DISPID_IHTMLELEMENT_INNERHTML.

## <a name="ddx_dhtml_elementinnertext"></a><a name="ddx_dhtml_elementinnertext"></a> DDX_DHtml_ElementInnerText

Définit ou récupère le texte entre les balises de début et de fin de l’élément actuel.

```
DDX_DHtml_ElementInnerText(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Paramètres

*DX*<br/>
Pointeur vers un objet [CDataExchange](../../mfc/reference/cdataexchange-class.md) .

*name*<br/>
Valeur que vous avez spécifiée pour le paramètre ID du contrôle HTML.

*var*<br/>
Valeur en cours d’échange.

### <a name="remarks"></a>Notes

Cette macro appelle la fonction [CDHtmlDialog ::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) à l’aide de l’ID de distribution DISPID_IHTMLELEMENT_INNERTEXT.

## <a name="ddx_dhtml_elementvalue"></a><a name="ddx_dhtml_elementvalue"></a> DDX_DHtml_ElementValue

Définit ou récupère la propriété de valeur à partir du contrôle sélectionné.

```
DDX_DHtml_ElementValue(
    CDataExchange* dx,
    LPCTSTR name,
    var)
```

#### <a name="parameters"></a>Paramètres

*DX*<br/>
Pointeur vers un objet [CDataExchange](../../mfc/reference/cdataexchange-class.md) .

*name*<br/>
Valeur que vous avez spécifiée pour le paramètre ID du contrôle HTML.

*var*<br/>
Valeur en cours d’échange. Consultez la *valeur* dans [CDHtmlDialog ::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext).

### <a name="remarks"></a>Notes

Cette macro ne fonctionnera que si elle est exécutée sur des contrôles qui ont une propriété de valeur. Les contrôles qui ont une propriété de valeur incluent les zones d’édition, les zones de liste et les zones de liste déroulante.

Cette macro appelle la fonction [CDHtmlDialog ::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) à l’aide de l’ID de distribution DISPID_A_VALUE.

## <a name="ddx_dhtml_frame_src"></a><a name="ddx_dhtml_frame_src"></a> DDX_DHtml_Frame_Src

Définit ou récupère l’URL du frame associé.

```
DDX_DHtml_Frame_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Paramètres

*DX*<br/>
Pointeur vers un objet [CDataExchange](../../mfc/reference/cdataexchange-class.md) .

*name*<br/>
Valeur que vous avez spécifiée pour le paramètre ID du contrôle HTML.

*var*<br/>
Valeur en cours d’échange.

### <a name="remarks"></a>Notes

Cette macro appelle la fonction [CDHtmlDialog ::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) à l’aide de l’ID de distribution DISPID_IHTMLFRAMEBASE_SRC.

## <a name="ddx_dhtml_iframe_src"></a><a name="ddx_dhtml_iframe_src"></a> DDX_DHtml_IFrame_Src

Définit ou récupère l’URL du frame associé.

```
DDX_DHtml_IFrame_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Paramètres

*DX*<br/>
Pointeur vers un objet [CDataExchange](../../mfc/reference/cdataexchange-class.md) .

*name*<br/>
Valeur que vous avez spécifiée pour le paramètre ID du contrôle HTML.

*var*<br/>
Valeur en cours d’échange.

### <a name="remarks"></a>Notes

Cette macro appelle la fonction [CDHtmlDialog ::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) à l’aide de l’ID de distribution DISPID_IHTMLFRAMEBASE_SRC.

## <a name="ddx_dhtml_img_src"></a><a name="ddx_dhtml_img_src"></a> DDX_DHtml_Img_Src

Obtient ou récupère le nom d’une image ou d’un clip vidéo dans le document.

```
DDX_DHtml_Img_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Paramètres

*DX*<br/>
Pointeur vers un objet [CDataExchange](../../mfc/reference/cdataexchange-class.md) .

*name*<br/>
Valeur que vous avez spécifiée pour le paramètre ID du contrôle HTML.

*var*<br/>
Valeur en cours d’échange.

### <a name="remarks"></a>Notes

Lorsque vous utilisez la macro DDX_DHtml_Img_Src pour récupérer la propriété SRC d’un élément IMAGE, l’objet image Internet Explorer retourne l’URL entièrement échappée pour la source de l’image. Par exemple, si vous utilisez la macro DDX_DHtml_Img_Src pour définir la propriété SRC d’un élément IMAGE sur la chaîne « une image intéressante », quand vous récupérez cette propriété, Internet Explorer retourne la chaîne « res://d:\myapplication\myapp.exe/some%20interesting%20picture. ».

Cette macro appelle la fonction [CDHtmlDialog ::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) à l’aide de l’ID de distribution DISPID_IHTMLIMGELEMENT_SRC.

## <a name="see-also"></a>Voir aussi

[CDHtmlDialog, classe](../../mfc/reference/cdhtmldialog-class.md)
