---
title: DDX_DHtml Helper Macros
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
ms.openlocfilehash: e2deed5e3fb63f46d83cf4c6f0d3c13525e93a2b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50592531"
---
# <a name="ddxdhtml-helper-macros"></a>DDX_DHtml Helper Macros

Les macros d’assistance de DDX_DHtml permettent un accès facile aux propriétés des contrôles sur une page HTML couramment utilisés.

### <a name="data-exchange-macros"></a>Macros d’échange de données

|||
|-|-|
|[DDX_DHtml_ElementValue](#ddx_dhtml_elementvalue)|Définit ou récupère la valeur de propriété à partir du contrôle sélectionné.|
|[DDX_DHtml_ElementInnerText](#ddx_dhtml_elementinnertext)|Définit ou récupère le texte entre les balises de début et de fin de l’élément actuel.|
|[DDX_DHtml_ElementInnerHtml](#ddx_dhtml_elementinnerhtml)|Définit ou récupère le code HTML entre les balises de début et de fin de l’élément actuel.|
|[DDX_DHtml_Anchor_Href](#ddx_dhtml_anchor_href)|Définit ou récupère la destination URL ou point d’ancrage.|
|[DDX_DHtml_Anchor_Target](#ddx_dhtml_anchor_target)|Définit ou récupère la fenêtre ou frame cible.|
|[DDX_DHtml_Img_Src](#ddx_dhtml_img_src)|Définit ou récupère le nom d’une image ou un clip vidéo dans le document.|
|[DDX_DHtml_Frame_Src](#ddx_dhtml_frame_src)|Définit ou récupère l’URL de l’image associée.|
|[DDX_DHtml_IFrame_Src](#ddx_dhtml_iframe_src)|Définit ou récupère l’URL de l’image associée.|

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdhtml.h

## <a name="ddx_dhtml_anchor_href"></a> DDX_DHtml_Anchor_Href

Définit ou récupère la destination URL ou point d’ancrage.

```
DDX_DHtml_Anchor_Href(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Paramètres

*DX*<br/>
Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet.

*name*<br/>
La valeur que vous avez spécifié pour le paramètre d’ID du contrôle HTML.

*var*<br/>
La valeur qui est échangée.

## <a name="remarks"></a>Notes

Cette macro appelle le [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) ID de dispatch de fonction à l’aide de la DISPID_IHTMLANCHORELEMENT_HREF

## <a name="ddx_dhtml_anchor_target"></a>  DDX_DHtml_Anchor_Target

Définit ou récupère la fenêtre ou frame cible.

```
DDX_DHtml_Anchor_Target(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Paramètres

*DX*<br/>
Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet.

*name*<br/>
La valeur que vous avez spécifié pour le paramètre d’ID du contrôle HTML.

*var*<br/>
La valeur qui est échangée.

## <a name="remarks"></a>Notes

Cette macro appelle le [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) ID de dispatch de fonction à l’aide de la DISPID_IHTMLANCHORELEMENT_TARGET

## <a name="ddx_dhtml_elementinnerhtml"></a>  DDX_DHtml_ElementInnerHtml

Définit ou récupère le code HTML entre les balises de début et de fin de l’élément actuel.

```
DDX_DHtml_ElementInnerHtml(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Paramètres

*DX*<br/>
Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet.

*name*<br/>
La valeur que vous avez spécifié pour le paramètre d’ID du contrôle HTML.

*var*<br/>
La valeur qui est échangée.

## <a name="remarks"></a>Notes

Cette macro appelle le [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) ID de dispatch de fonction à l’aide de la DISPID_IHTMLELEMENT_INNERHTML

## <a name="ddx_dhtml_elementinnertext"></a>  DDX_DHtml_ElementInnerText

Définit ou récupère le texte entre les balises de début et de fin de l’élément actuel.

```
DDX_DHtml_ElementInnerText(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Paramètres

*DX*<br/>
Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet.

*name*<br/>
La valeur que vous avez spécifié pour le paramètre d’ID du contrôle HTML.

*var*<br/>
La valeur qui est échangée.

## <a name="remarks"></a>Notes

Cette macro appelle le [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) ID de dispatch de fonction à l’aide de la DISPID_IHTMLELEMENT_INNERTEXT

## <a name="ddx_dhtml_elementvalue"></a> DDX_DHtml_ElementValue

Définit ou récupère la valeur de propriété à partir du contrôle sélectionné.

```
DDX_DHtml_ElementValue(
    CDataExchange* dx,
    LPCTSTR name,
    var)
```

#### <a name="parameters"></a>Paramètres

*DX*<br/>
Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet.

*name*<br/>
La valeur que vous avez spécifié pour le paramètre d’ID du contrôle HTML.

*var*<br/>
La valeur qui est échangée. Consultez *valeur* dans [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext).

## <a name="remarks"></a>Notes

Cette macro réussira uniquement lors de l’exécuter sur les contrôles qui ont une propriété de valeur. Contrôles qui ont une valeur de propriété incluent des zones d’édition, zones de liste et zones de liste déroulante.

Cette macro appelle le [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) ID de dispatch de fonction à l’aide de la DISPID_A_VALUE

## <a name="ddx_dhtml_frame_src"></a> DDX_DHtml_Frame_Src

Définit ou récupère l’URL de l’image associée.

```
DDX_DHtml_Frame_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Paramètres

*DX*<br/>
Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet.

*name*<br/>
La valeur que vous avez spécifié pour le paramètre d’ID du contrôle HTML.

*var*<br/>
La valeur qui est échangée.

## <a name="remarks"></a>Notes

Cette macro appelle le [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) ID de dispatch de fonction à l’aide de la DISPID_IHTMLFRAMEBASE_SRC

## <a name="ddx_dhtml_iframe_src"></a> DDX_DHtml_IFrame_Src

Définit ou récupère l’URL de l’image associée.

```
DDX_DHtml_IFrame_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Paramètres

*DX*<br/>
Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet.

*name*<br/>
La valeur que vous avez spécifié pour le paramètre d’ID du contrôle HTML.

*var*<br/>
La valeur qui est échangée.

## <a name="remarks"></a>Notes

Cette macro appelle le [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) ID de dispatch de fonction à l’aide de la DISPID_IHTMLFRAMEBASE_SRC

## <a name="ddx_dhtml_img_src"></a>DDX_DHtml_Img_Src

Obtient ou récupère le nom d’une image ou un clip vidéo dans le document.

```
DDX_DHtml_Img_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Paramètres

*DX*<br/>
Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet.

*name*<br/>
La valeur que vous avez spécifié pour le paramètre d’ID du contrôle HTML.

*var*<br/>
La valeur qui est échangée.

## <a name="remarks"></a>Notes

Lorsque vous utilisez la macro DDX_DHtml_Img_Src pour récupérer la propriété src d’un élément IMAGE, l’objet d’image de Internet Explorer renvoie l’URL entièrement avec séquence d’échappement pour la source de l’image. Par exemple, si vous utilisez la macro DDX_DHtml_Img_Src pour définir la propriété de src d’un élément d’IMAGE à la chaîne « certains image intéressante », lorsque vous récupérez cette propriété, Internet Explorer retourne la chaîne « res://d:\myapplication\myapp.exe/some% 20interesting % 20picture. »

Cette macro appelle le [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) ID de dispatch de fonction à l’aide de la DISPID_IHTMLIMGELEMENT_SRC

## <a name="see-also"></a>Voir aussi

[CDHtmlDialog, classe](../../mfc/reference/cdhtmldialog-class.md)
