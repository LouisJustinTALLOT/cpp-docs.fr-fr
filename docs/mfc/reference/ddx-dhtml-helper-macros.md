---
title: DDX_DHtml Helper, structure
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
ms.openlocfilehash: f78a923a498713867c13ccc88e3e30c1f0a23885
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365873"
---
# <a name="ddx_dhtml-helper-macros"></a>DDX_DHtml Helper, structure

Les macros d’aide DDX_DHtml permettent un accès facile aux propriétés couramment utilisées des contrôles sur une page HTML.

### <a name="data-exchange-macros"></a>Macros d’échange de données

|||
|-|-|
|[DDX_DHtml_ElementValue](#ddx_dhtml_elementvalue)|Définit ou récupère la propriété Value à partir du contrôle sélectionné.|
|[DDX_DHtml_ElementInnerText](#ddx_dhtml_elementinnertext)|Définit ou récupère le texte entre les balises de démarrage et de fin de l’élément actuel.|
|[DDX_DHtml_ElementInnerHtml](#ddx_dhtml_elementinnerhtml)|Définit ou récupère le HTML entre les balises de démarrage et de fin de l’élément actuel.|
|[DDX_DHtml_Anchor_Href](#ddx_dhtml_anchor_href)|Définit ou récupère l’URL de destination ou le point d’ancrage.|
|[DDX_DHtml_Anchor_Target](#ddx_dhtml_anchor_target)|Définit ou récupère la fenêtre ou le cadre cible.|
|[DDX_DHtml_Img_Src](#ddx_dhtml_img_src)|Définit ou récupère le nom d’une image ou d’un clip vidéo dans le document.|
|[DDX_DHtml_Frame_Src](#ddx_dhtml_frame_src)|Définit ou récupère l’URL du cadre associé.|
|[DDX_DHtml_IFrame_Src](#ddx_dhtml_iframe_src)|Définit ou récupère l’URL du cadre associé.|

## <a name="requirements"></a>Spécifications

**En-tête:** afxdhtml.h

## <a name="ddx_dhtml_anchor_href"></a><a name="ddx_dhtml_anchor_href"></a>DDX_DHtml_Anchor_Href

Définit ou récupère l’URL de destination ou le point d’ancrage.

```
DDX_DHtml_Anchor_Href(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Paramètres

*Dx*<br/>
Un pointeur à un objet [CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*name*<br/>
La valeur que vous avez spécifiée pour le paramètre d’identification du contrôle HTML.

*Var*<br/>
La valeur échangée.

## <a name="remarks"></a>Notes

Cette macro appelle la fonction [CDHtmlDialog::DDX-DHtml-ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) à l’aide de l’ID de répartition DISPID_IHTMLANCHORELEMENT_HREF.

## <a name="ddx_dhtml_anchor_target"></a><a name="ddx_dhtml_anchor_target"></a>DDX_DHtml_Anchor_Target

Définit ou récupère la fenêtre ou le cadre cible.

```
DDX_DHtml_Anchor_Target(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Paramètres

*Dx*<br/>
Un pointeur à un objet [CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*name*<br/>
La valeur que vous avez spécifiée pour le paramètre d’identification du contrôle HTML.

*Var*<br/>
La valeur échangée.

## <a name="remarks"></a>Notes

Cette macro appelle la fonction [CDHtmlDialog::DDX-DHtml-ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) à l’aide de l’ID de répartition DISPID_IHTMLANCHORELEMENT_TARGET.

## <a name="ddx_dhtml_elementinnerhtml"></a><a name="ddx_dhtml_elementinnerhtml"></a>DDX_DHtml_ElementInnerHtml

Définit ou récupère le HTML entre les balises de démarrage et de fin de l’élément actuel.

```
DDX_DHtml_ElementInnerHtml(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Paramètres

*Dx*<br/>
Un pointeur à un objet [CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*name*<br/>
La valeur que vous avez spécifiée pour le paramètre d’identification du contrôle HTML.

*Var*<br/>
La valeur échangée.

## <a name="remarks"></a>Notes

Cette macro appelle la fonction [CDHtmlDialog::DDX-DHtml-ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) à l’aide de l’ID de répartition DISPID_IHTMLELEMENT_INNERHTML.

## <a name="ddx_dhtml_elementinnertext"></a><a name="ddx_dhtml_elementinnertext"></a>DDX_DHtml_ElementInnerText

Définit ou récupère le texte entre les balises de démarrage et de fin de l’élément actuel.

```
DDX_DHtml_ElementInnerText(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Paramètres

*Dx*<br/>
Un pointeur à un objet [CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*name*<br/>
La valeur que vous avez spécifiée pour le paramètre d’identification du contrôle HTML.

*Var*<br/>
La valeur échangée.

## <a name="remarks"></a>Notes

Cette macro appelle la fonction [CDHtmlDialog::DDX-DHtml-ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) à l’aide de l’ID de répartition DISPID_IHTMLELEMENT_INNERTEXT.

## <a name="ddx_dhtml_elementvalue"></a><a name="ddx_dhtml_elementvalue"></a>DDX_DHtml_ElementValue

Définit ou récupère la propriété Value à partir du contrôle sélectionné.

```
DDX_DHtml_ElementValue(
    CDataExchange* dx,
    LPCTSTR name,
    var)
```

#### <a name="parameters"></a>Paramètres

*Dx*<br/>
Un pointeur à un objet [CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*name*<br/>
La valeur que vous avez spécifiée pour le paramètre d’identification du contrôle HTML.

*Var*<br/>
La valeur échangée. Voir *la valeur* dans [CDHtmlDialog::DDX-DHtml-ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext).

## <a name="remarks"></a>Notes

Cette macro ne réussira que lorsqu’elle sera exécutée sur des contrôles qui ont une propriété de valeur. Les contrôles qui ont une propriété De valeur incluent des boîtes d’édition, des boîtes de liste, et des boîtes de combo.

Cette macro appelle la fonction [CDHtmlDialog::DDX-DHtml-ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) à l’aide de l’ID de répartition DISPID_A_VALUE.

## <a name="ddx_dhtml_frame_src"></a><a name="ddx_dhtml_frame_src"></a>DDX_DHtml_Frame_Src

Définit ou récupère l’URL du cadre associé.

```
DDX_DHtml_Frame_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Paramètres

*Dx*<br/>
Un pointeur à un objet [CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*name*<br/>
La valeur que vous avez spécifiée pour le paramètre d’identification du contrôle HTML.

*Var*<br/>
La valeur échangée.

## <a name="remarks"></a>Notes

Cette macro appelle la fonction [CDHtmlDialog::DDX-DHtml-ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) à l’aide de l’ID de répartition DISPID_IHTMLFRAMEBASE_SRC.

## <a name="ddx_dhtml_iframe_src"></a><a name="ddx_dhtml_iframe_src"></a>DDX_DHtml_IFrame_Src

Définit ou récupère l’URL du cadre associé.

```
DDX_DHtml_IFrame_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Paramètres

*Dx*<br/>
Un pointeur à un objet [CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*name*<br/>
La valeur que vous avez spécifiée pour le paramètre d’identification du contrôle HTML.

*Var*<br/>
La valeur échangée.

## <a name="remarks"></a>Notes

Cette macro appelle la fonction [CDHtmlDialog::DDX-DHtml-ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) à l’aide de l’ID de répartition DISPID_IHTMLFRAMEBASE_SRC.

## <a name="ddx_dhtml_img_src"></a><a name="ddx_dhtml_img_src"></a>DDX_DHtml_Img_Src

Obtient ou récupère le nom d’une image ou d’un clip vidéo dans le document.

```
DDX_DHtml_Img_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Paramètres

*Dx*<br/>
Un pointeur à un objet [CDataExchange.](../../mfc/reference/cdataexchange-class.md)

*name*<br/>
La valeur que vous avez spécifiée pour le paramètre d’identification du contrôle HTML.

*Var*<br/>
La valeur échangée.

## <a name="remarks"></a>Notes

Lors de l’utilisation de la macro DDX_DHtml_Img_Src pour récupérer la propriété de src pour un élément IMAGE, l’objet d’image Internet Explorer retournera l’URL entièrement échappée pour la source d’image. Par exemple, si vous utilisez la macro DDX_DHtml_Img_Src pour définir la propriété de src d’un élément IMAGE à la chaîne "une image intéressante," lorsque vous récupérez cette propriété, Internet Explorer retournera la chaîne "res://d:myapplication-myapp.exe/some%20interesting%20picture."

Cette macro appelle la fonction [CDHtmlDialog::DDX-DHtml-ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) à l’aide de l’ID de répartition DISPID_IHTMLIMGELEMENT_SRC.

## <a name="see-also"></a>Voir aussi

[CDHtmlDialog, classe](../../mfc/reference/cdhtmldialog-class.md)
