---
title: Classe de CD2DTextFormat | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DTextFormat
- AFXRENDERTARGET/CD2DTextFormat
- AFXRENDERTARGET/CD2DTextFormat::CD2DTextFormat
- AFXRENDERTARGET/CD2DTextFormat::Create
- AFXRENDERTARGET/CD2DTextFormat::Destroy
- AFXRENDERTARGET/CD2DTextFormat::Get
- AFXRENDERTARGET/CD2DTextFormat::GetFontFamilyName
- AFXRENDERTARGET/CD2DTextFormat::GetLocaleName
- AFXRENDERTARGET/CD2DTextFormat::IsValid
- AFXRENDERTARGET/CD2DTextFormat::ReCreate
- AFXRENDERTARGET/CD2DTextFormat::m_pTextFormat
dev_langs:
- C++
helpviewer_keywords:
- CD2DTextFormat [MFC], CD2DTextFormat
- CD2DTextFormat [MFC], Create
- CD2DTextFormat [MFC], Destroy
- CD2DTextFormat [MFC], Get
- CD2DTextFormat [MFC], GetFontFamilyName
- CD2DTextFormat [MFC], GetLocaleName
- CD2DTextFormat [MFC], IsValid
- CD2DTextFormat [MFC], ReCreate
- CD2DTextFormat [MFC], m_pTextFormat
ms.assetid: db194cec-9dae-4644-ab84-7c43b7164117
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8e55689fa71ed5f0e4ebd4978a004212d5fb82b5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352888"
---
# <a name="cd2dtextformat-class"></a>CD2DTextFormat, classe
Wrapper pour IDWriteTextFormat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CD2DTextFormat : public CD2DResource;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CD2DTextFormat::CD2DTextFormat](#cd2dtextformat)|Construit un objet CD2DTextFormat.|  
|[CD2DTextFormat :: ~ CD2DTextFormat](#cd2dtextformat__~cd2dtextformat)|Destructeur. Appelé lorsqu’un objet de format de texte D2D est détruit.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CD2DTextFormat::Create](#create)|Crée un CD2DTextFormat. (Substitue [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|  
|[CD2DTextFormat::Destroy](#destroy)|Détruit un objet CD2DTextFormat. (Substitue [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|  
|[CD2DTextFormat::Get](#get)|Renvoie l’interface IDWriteTextFormat|  
|[CD2DTextFormat::GetFontFamilyName](#getfontfamilyname)|Obtient une copie du nom de famille de polices.|  
|[CD2DTextFormat::GetLocaleName](#getlocalename)|Obtient une copie du nom des paramètres régionaux.|  
|[CD2DTextFormat::IsValid](#isvalid)|Vérifie la validité des ressources (remplace [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|  
|[CD2DTextFormat::ReCreate](#recreate)|Crée de nouveau un CD2DTextFormat. (Substitue [CD2DResource::ReCreate](../../mfc/reference/cd2dresource-class.md#recreate).)|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CD2DTextFormat::operator IDWriteTextFormat *](#operator_idwritetextformat_star)|Renvoie l’interface IDWriteTextFormat|  
  
### <a name="protected-data-members"></a>Membres de données protégés  
  
|Name|Description|  
|----------|-----------------|  
|[CD2DTextFormat::m_pTextFormat](#m_ptextformat)|Pointeur vers un IDWriteTextFormat.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DTextFormat](../../mfc/reference/cd2dtextformat-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxrendertarget.h  
  
##  <a name="_dtorcd2dtextformat"></a>  CD2DTextFormat :: ~ CD2DTextFormat  
 Destructeur. Appelé lorsqu’un objet de format de texte D2D est détruit.  
  
```  
virtual ~CD2DTextFormat();
```  
  
##  <a name="cd2dtextformat"></a>  CD2DTextFormat::CD2DTextFormat  
 Construit un objet CD2DTextFormat.  
  
```  
CD2DTextFormat(
    CRenderTarget* pParentTarget,  
    const CString& strFontFamilyName,  
    FLOAT fontSize,  
    DWRITE_FONT_WEIGHT fontWeight = DWRITE_FONT_WEIGHT_NORMAL,  
    DWRITE_FONT_STYLE fontStyle = DWRITE_FONT_STYLE_NORMAL,  
    DWRITE_FONT_STRETCH fontStretch = DWRITE_FONT_STRETCH_NORMAL,  
    const CString& strFontLocale = _T(""),  
    IDWriteFontCollection* pFontCollection = NULL,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 `pParentTarget`  
 Pointeur vers la cible de rendu.  
  
 `strFontFamilyName`  
 Un objet CString qui contient le nom de la famille de polices.  
  
 `fontSize`  
 La taille logique de la police en DIP (« pixels indépendants du périphérique ») unités. Une DIP est égal à 1/96e de pouce.  
  
 `fontWeight`  
 Une valeur qui indique l’épaisseur de police pour l’objet texte.  
  
 `fontStyle`  
 Une valeur qui indique le style de police pour l’objet texte.  
  
 `fontStretch`  
 Une valeur qui indique l’étirement de police pour l’objet texte.  
  
 `strFontLocale`  
 Un objet CString qui contient le nom des paramètres régionaux.  
  
 `pFontCollection`  
 Pointeur vers un objet de collection de polices. Lorsque ce paramètre est NULL, indique la collection de polices système.  
  
 `bAutoDestroy`  
 Indique que l’objet sera détruit par le propriétaire (pParentTarget).  
  
##  <a name="create"></a>  CD2DTextFormat::Create  
 Crée un CD2DTextFormat.  
  
```  
virtual HRESULT Create(CRenderTarget* */);
```  
  
### <a name="return-value"></a>Valeur de retour  
 Si la méthode réussit, elle retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.  
  
##  <a name="destroy"></a>  CD2DTextFormat::Destroy  
 Détruit un objet CD2DTextFormat.  
  
```  
virtual void Destroy();
```  
  
##  <a name="get"></a>  CD2DTextFormat::Get  
 Renvoie l’interface IDWriteTextFormat  
  
```  
IDWriteTextFormat* Get();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers une interface de IDWriteTextFormat ou NULL si l’objet n’est pas encore initialisé.  
  
##  <a name="getfontfamilyname"></a>  CD2DTextFormat::GetFontFamilyName  
 Obtient une copie du nom de famille de polices.  
  
```  
CString GetFontFamilyName() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Objet CString qui contient le nom de famille de polices en cours.  
  
##  <a name="getlocalename"></a>  CD2DTextFormat::GetLocaleName  
 Obtient une copie du nom des paramètres régionaux.  
  
```  
CString GetLocaleName() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Objet CString qui contient le nom de paramètres régionaux actuel.  
  
##  <a name="isvalid"></a>  CD2DTextFormat::IsValid  
 Vérifications de validité des ressources  
  
```  
virtual BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si la ressource est valide ; Sinon, FALSE.  
  
##  <a name="m_ptextformat"></a>  CD2DTextFormat::m_pTextFormat  
 Pointeur vers un IDWriteTextFormat.  
  
```  
IDWriteTextFormat* m_pTextFormat;  
```  
  
##  <a name="operator_idwritetextformat_star"></a>  CD2DTextFormat::operator IDWriteTextFormat *  
 Renvoie l’interface IDWriteTextFormat  
  
```  
operator IDWriteTextFormat*();
```   
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers une interface de IDWriteTextFormat ou NULL si l’objet n’est pas encore initialisé.  
  
##  <a name="recreate"></a>  CD2DTextFormat::ReCreate  
 Crée de nouveau un CD2DTextFormat.  
  
```  
virtual HRESULT ReCreate(CRenderTarget* */);
```  
  
### <a name="return-value"></a>Valeur de retour  
 Si la méthode réussit, elle retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.  
  
## <a name="see-also"></a>Voir aussi  
 [Classes](../../mfc/reference/mfc-classes.md)
