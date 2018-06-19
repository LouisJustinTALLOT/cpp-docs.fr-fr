---
title: Macros d’assistance de DDX_DHtml | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- AFXDHTML/DDX_DHtml_ElementValue
- AFXDHTML/DDX_DHtml_ElementInnerText
- AFXDHTML/DDX_DHtml_ElementInnerHtml
- AFXDHTML/DDX_DHtml_Anchor_Href
- AFXDHTML/DDX_DHtml_Anchor_Target
- AFXDHTML/DDX_DHtml_Img_Src
- AFXDHTML/DDX_DHtml_Frame_Src
- AFXDHTML/DDX_DHtml_IFrame_Src
dev_langs:
- C++
helpviewer_keywords:
- macros [MFC], exchanging data with HMTL pages
- DDX macros [MFC]
- HTML pages [MFC], helper macros
- DDX (dialog data exchange), DHtml helper macros
- macros [MFC], DDX_DHtml helpers
ms.assetid: c46302d2-ea43-4fea-bfc2-6f590d99f267
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb2e9d2494463b502fda85c03fa1b861e1182cfc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33372073"
---
# <a name="ddxdhtml-helper-macros"></a>Macros d’assistance DDX_DHtml
Les macros d’assistance de DDX_DHtml permettent un accès facile aux propriétés courantes des contrôles sur une page HTML.  
  
### <a name="data-exchange-macros"></a>Macros d’échange de données  
  
|||  
|-|-|  
|[DDX_DHtml_ElementValue](#ddx_dhtml_elementvalue)|Définit ou récupère la propriété de valeur à partir du contrôle sélectionné.|  
|[DDX_DHtml_ElementInnerText](#ddx_dhtml_elementinnertext)|Définit ou récupère le texte entre les balises de début et de fin de l’élément actuel.|  
|[DDX_DHtml_ElementInnerHtml](#ddx_dhtml_elementinnerhtml)|Définit ou récupère le code HTML entre les balises de début et de fin de l’élément actuel.|  
|[DDX_DHtml_Anchor_Href](#ddx_dhtml_anchor_href)|Définit ou récupère la destination URL ou point d’ancrage.|  
|[DDX_DHtml_Anchor_Target](#ddx_dhtml_anchor_target)|Définit ou récupère la fenêtre ou frame cible.|  
|[DDX_DHtml_Img_Src](#ddx_dhtml_img_src)|Définit ou récupère le nom d’une image ou un clip vidéo dans le document.|  
|[DDX_DHtml_Frame_Src](#ddx_dhtml_frame_src)|Définit ou récupère l’URL de l’image associée.|  
|[DDX_DHtml_IFrame_Src](#ddx_dhtml_iframe_src)|Définit ou récupère l’URL de l’image associée.|  
  
## <a name="requirements"></a>Spécifications  
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
 `dx`  
 Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet.  
  
 `name`  
 La valeur que vous avez spécifié pour le paramètre d’ID du contrôle HTML.  
  
 `var`  
 La valeur qui est échangée.  
  
## <a name="remarks"></a>Notes  
 Cette macro appelle la [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) ID de distribution à l’aide de la DISPID_IHTMLANCHORELEMENT_HREF (fonction)

## <a name="ddx_dhtml_anchor_target"></a>  DDX_DHtml_Anchor_Target
 Définit ou récupère la fenêtre ou frame cible.  
    
```  
DDX_DHtml_Anchor_Target(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dx`  
 Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet.  
  
 `name`  
 La valeur que vous avez spécifié pour le paramètre d’ID du contrôle HTML.  
  
 `var`  
 La valeur qui est échangée.  
  
## <a name="remarks"></a>Notes  
 Cette macro appelle la [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) ID de distribution à l’aide de la DISPID_IHTMLANCHORELEMENT_TARGET (fonction)  

## <a name="ddx_dhtml_elementinnerhtml"></a>  DDX_DHtml_ElementInnerHtml
 Définit ou récupère le code HTML entre les balises de début et de fin de l’élément actuel.  
  
  
  
```  
DDX_DHtml_ElementInnerHtml(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dx`  
 Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet.  
  
 `name`  
 La valeur que vous avez spécifié pour le paramètre d’ID du contrôle HTML.  
  
 `var`  
 La valeur qui est échangée.  
  
## <a name="remarks"></a>Notes  
 Cette macro appelle la [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) ID de distribution à l’aide de la DISPID_IHTMLELEMENT_INNERHTML (fonction)  
  

## <a name="ddx_dhtml_elementinnertext"></a>  DDX_DHtml_ElementInnerText
Définit ou récupère le texte entre les balises de début et de fin de l’élément actuel.  
  
  
  
```  
DDX_DHtml_ElementInnerText(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dx`  
 Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet.  
  
 `name`  
 La valeur que vous avez spécifié pour le paramètre d’ID du contrôle HTML.  
  
 `var`  
 La valeur qui est échangée.  
  
## <a name="remarks"></a>Notes  
 Cette macro appelle la [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) ID de distribution à l’aide de la DISPID_IHTMLELEMENT_INNERTEXT (fonction) 

## <a name="ddx_dhtml_elementvalue"></a> DDX_DHtml_ElementValue  
Définit ou récupère la propriété de valeur à partir du contrôle sélectionné.  
 
```  
DDX_DHtml_ElementValue(
    CDataExchange* dx,  
    LPCTSTR name,
    var)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dx`  
 Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet.  
  
 `name`  
 La valeur que vous avez spécifié pour le paramètre d’ID du contrôle HTML.  
  
 `var`  
 La valeur qui est échangée. Consultez *valeur* dans [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext).  
  
## <a name="remarks"></a>Notes  
 Cette macro réussit uniquement lors de l’exécuter sur des contrôles qui ont une propriété de valeur. Les contrôles qui ont une valeur de propriété incluent des zones d’édition, zones de liste et zones de liste déroulante.  
  
 Cette macro appelle la [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) ID de distribution à l’aide de la DISPID_A_VALUE (fonction)  

## <a name="ddx_dhtml_frame_src"></a> DDX_DHtml_Frame_Src
Définit ou récupère l’URL de l’image associée.  
  
```  
DDX_DHtml_Frame_Src(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dx`  
 Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet.  
  
 `name`  
 La valeur que vous avez spécifié pour le paramètre d’ID du contrôle HTML.  
  
 `var`  
 La valeur qui est échangée.  
  
## <a name="remarks"></a>Notes  
 Cette macro appelle la [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) ID de distribution à l’aide de la DISPID_IHTMLFRAMEBASE_SRC (fonction)  

## <a name="ddx_dhtml_iframe_src"></a> DDX_DHtml_IFrame_Src
Définit ou récupère l’URL de l’image associée.  
  
  
  
```  
DDX_DHtml_IFrame_Src(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dx`  
 Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet.  
  
 `name`  
 La valeur que vous avez spécifié pour le paramètre d’ID du contrôle HTML.  
  
 `var`  
 La valeur qui est échangée.  
  
## <a name="remarks"></a>Notes  
 Cette macro appelle la [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) ID de distribution à l’aide de la DISPID_IHTMLFRAMEBASE_SRC (fonction) 

## <a name="ddx_dhtml_img_src"></a>DDX_DHtml_Img_Src
Obtient ou récupère le nom d’une image ou un clip vidéo dans le document.  
  
```  
DDX_DHtml_Img_Src(
    CDataExchange* dx,  
    LPCTSTR name,  
    CString& var)  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dx`  
 Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet.  
  
 `name`  
 La valeur que vous avez spécifié pour le paramètre d’ID du contrôle HTML.  
  
 `var`  
 La valeur qui est échangée.  
  
## <a name="remarks"></a>Notes  
 Lorsque vous utilisez la `DDX_DHtml_Img_Src` (macro) pour récupérer la propriété src d’un élément d’IMAGE, l’objet d’image Internet Explorer renvoie l’URL complète avec séquence d’échappement pour la source de l’image. Par exemple, si vous utilisez la `DDX_DHtml_Img_Src` macro pour définir la propriété src d’un élément d’IMAGE à la chaîne « certains image intéressante », lorsque vous récupérez cette propriété, Internet Explorer retourne la chaîne « res://d:\myapplication\myapp.exe/some% 20interesting % 20picture. »  
  
 Cette macro appelle la [CDHtmlDialog::DDX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) ID de distribution à l’aide de la DISPID_IHTMLIMGELEMENT_SRC (fonction)  

  
## <a name="see-also"></a>Voir aussi  
 [CDHtmlDialog, classe](../../mfc/reference/cdhtmldialog-class.md)
