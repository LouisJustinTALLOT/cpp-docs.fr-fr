---
title: Classe de CD2DTextLayout | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout::CD2DTextLayout
- AFXRENDERTARGET/CD2DTextLayout::Create
- AFXRENDERTARGET/CD2DTextLayout::Destroy
- AFXRENDERTARGET/CD2DTextLayout::Get
- AFXRENDERTARGET/CD2DTextLayout::GetFontFamilyName
- AFXRENDERTARGET/CD2DTextLayout::GetLocaleName
- AFXRENDERTARGET/CD2DTextLayout::IsValid
- AFXRENDERTARGET/CD2DTextLayout::ReCreate
- AFXRENDERTARGET/CD2DTextLayout::SetFontFamilyName
- AFXRENDERTARGET/CD2DTextLayout::SetLocaleName
- AFXRENDERTARGET/CD2DTextLayout::m_pTextLayout
dev_langs:
- C++
helpviewer_keywords:
- CD2DTextLayout [MFC], CD2DTextLayout
- CD2DTextLayout [MFC], Create
- CD2DTextLayout [MFC], Destroy
- CD2DTextLayout [MFC], Get
- CD2DTextLayout [MFC], GetFontFamilyName
- CD2DTextLayout [MFC], GetLocaleName
- CD2DTextLayout [MFC], IsValid
- CD2DTextLayout [MFC], ReCreate
- CD2DTextLayout [MFC], SetFontFamilyName
- CD2DTextLayout [MFC], SetLocaleName
- CD2DTextLayout [MFC], m_pTextLayout
ms.assetid: 724bd13c-f2ef-4e55-a775-8cb04b7b7908
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 343d56ebf3f92dadeb286ae2fa44b6e735498215
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355923"
---
# <a name="cd2dtextlayout-class"></a>CD2DTextLayout, classe
Wrapper pour IDWriteTextLayout.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CD2DTextLayout : public CD2DResource;  
```  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CD2DTextLayout::CD2DTextLayout](#cd2dtextlayout)|Construit un objet CD2DTextLayout.|  
|[CD2DTextLayout :: ~ CD2DTextLayout](#cd2dtextlayout__~cd2dtextlayout)|Destructeur. Appelé lorsqu’un objet de mise en page de texte D2D est détruit.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CD2DTextLayout::Create](#create)|Crée un CD2DTextLayout. (Substitue [CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create).)|  
|[CD2DTextLayout::Destroy](#destroy)|Détruit un objet CD2DTextLayout. (Substitue [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|  
|[CD2DTextLayout::Get](#get)|Renvoie l’interface IDWriteTextLayout|  
|[CD2DTextLayout::GetFontFamilyName](#getfontfamilyname)|Copie le nom de famille de polices du texte à la position spécifiée.|  
|[CD2DTextLayout::GetLocaleName](#getlocalename)|Obtient le nom des paramètres régionaux du texte à la position spécifiée.|  
|[CD2DTextLayout::IsValid](#isvalid)|Vérifie la validité des ressources (remplace [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|  
|[CD2DTextLayout::ReCreate](#recreate)|Crée de nouveau un CD2DTextLayout. (Substitue [CD2DResource::ReCreate](../../mfc/reference/cd2dresource-class.md#recreate).)|  
|[CD2DTextLayout::SetFontFamilyName](#setfontfamilyname)|Définit le nom famille se terminant par null de police du texte dans une plage de texte spécifiée|  
|[CD2DTextLayout::SetLocaleName](#setlocalename)|Définit le nom de paramètres régionaux pour le texte dans une plage de texte spécifiée|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CD2DTextLayout::operator IDWriteTextLayout *](#operator_idwritetextlayout_star)|Renvoie l’interface IDWriteTextLayout|  
  
### <a name="protected-data-members"></a>Membres de données protégés  
  
|Name|Description|  
|----------|-----------------|  
|[CD2DTextLayout::m_pTextLayout](#m_ptextlayout)|Pointeur vers un IDWriteTextLayout.|  
  
## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DTextLayout](../../mfc/reference/cd2dtextlayout-class.md)  
  
## <a name="requirements"></a>Spécifications  
 **En-tête :** afxrendertarget.h  
  
##  <a name="_dtorcd2dtextlayout"></a>  CD2DTextLayout :: ~ CD2DTextLayout  
 Destructeur. Appelé lorsqu’un objet de mise en page de texte D2D est détruit.  
  
```  
virtual ~CD2DTextLayout();
```  
  
##  <a name="cd2dtextlayout"></a>  CD2DTextLayout::CD2DTextLayout  
 Construit un objet CD2DTextLayout.  
  
```  
CD2DTextLayout(
    CRenderTarget* pParentTarget,  
    const CString& strText,  
    CD2DTextFormat& textFormat,  
    const CD2DSizeF& sizeMax,  
    BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>Paramètres  
 `pParentTarget`  
 Pointeur vers la cible de rendu.  
  
 `strText`  
 Un objet CString qui contient la chaîne pour créer un nouvel objet CD2DTextLayout à partir de.  
  
 `textFormat`  
 Un objet CString qui contient le format à appliquer à la chaîne.  
  
 `sizeMax`  
 La taille de la zone de disposition.  
  
 `bAutoDestroy`  
 Indique que l’objet sera détruit par le propriétaire (pParentTarget).  
  
##  <a name="create"></a>  CD2DTextLayout::Create  
 Crée un CD2DTextLayout.  
  
```  
virtual HRESULT Create(CRenderTarget* */);
```  
  
### <a name="return-value"></a>Valeur de retour  
 Si la méthode réussit, elle retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.  
  
##  <a name="destroy"></a>  CD2DTextLayout::Destroy  
 Détruit un objet CD2DTextLayout.  
  
```  
virtual void Destroy();
```  
  
##  <a name="get"></a>  CD2DTextLayout::Get  
 Renvoie l’interface IDWriteTextLayout  
  
```  
IDWriteTextLayout* Get();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers une interface de IDWriteTextLayout ou NULL si l’objet n’est pas encore initialisé.  
  
##  <a name="getfontfamilyname"></a>  CD2DTextLayout::GetFontFamilyName  
 Copie le nom de famille de polices du texte à la position spécifiée.  
  
```  
CString GetFontFamilyName(
    UINT32 currentPosition,  
    DWRITE_TEXT_RANGE* textRange = NULL) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `currentPosition`  
 La position du texte à examiner.  
  
 `textRange`  
 La plage de texte qui a la même mise en forme en tant que le texte à la position spécifiée par la position actuelle. Cela signifie que l’exécution a la mise en forme exacte que la position spécifiée, y compris de manière non limitative, le nom de famille de polices.  
  
### <a name="return-value"></a>Valeur de retour  
 Objet CString qui contient le nom de famille de polices en cours.  
  
##  <a name="getlocalename"></a>  CD2DTextLayout::GetLocaleName  
 Obtient le nom des paramètres régionaux du texte à la position spécifiée.  
  
```  
CString GetLocaleName(
    UINT32 currentPosition,  
    DWRITE_TEXT_RANGE* textRange = NULL) const;  
```  
  
### <a name="parameters"></a>Paramètres  
 `currentPosition`  
 La position du texte à inspecter.  
  
 `textRange`  
 La plage de texte qui a la même mise en forme en tant que le texte à la position spécifiée par la position actuelle. Cela signifie que l’exécution a la mise en forme exacte que la position spécifiée, y compris de manière non limitative, le nom des paramètres régionaux.  
  
### <a name="return-value"></a>Valeur de retour  
 Objet CString qui contient le nom de paramètres régionaux actuel.  
  
##  <a name="isvalid"></a>  CD2DTextLayout::IsValid  
 Vérifications de validité des ressources  
  
```  
virtual BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 TRUE si la ressource est valide ; Sinon, FALSE.  
  
##  <a name="m_ptextlayout"></a>  CD2DTextLayout::m_pTextLayout  
 Pointeur vers un IDWriteTextLayout.  
  
```  
IDWriteTextLayout* m_pTextLayout;  
```  
  
##  <a name="operator_idwritetextlayout_star"></a>  CD2DTextLayout::operator IDWriteTextLayout *  
 Renvoie l’interface IDWriteTextLayout  
  
```  
operator IDWriteTextLayout*();
```   
  
### <a name="return-value"></a>Valeur de retour  
 Pointeur vers une interface de IDWriteTextLayout ou NULL si l’objet n’est pas encore initialisé.  
  
##  <a name="recreate"></a>  CD2DTextLayout::ReCreate  
 Crée de nouveau un CD2DTextLayout.  
  
```  
virtual HRESULT ReCreate(CRenderTarget* */);
```  
  
### <a name="return-value"></a>Valeur de retour  
 Si la méthode réussit, elle retourne S_OK. Sinon, elle retourne un code d’erreur HRESULT.  
  
##  <a name="setfontfamilyname"></a>  CD2DTextLayout::SetFontFamilyName  
 Définit le nom famille se terminant par null de police du texte dans une plage de texte spécifiée  
  
```  
BOOL SetFontFamilyName(
    LPCWSTR pwzFontFamilyName,  
    DWRITE_TEXT_RANGE textRange);
```  
  
### <a name="parameters"></a>Paramètres  
 `pwzFontFamilyName`  
 Le nom de famille de polices qui s’applique à la chaîne de caractères dans la plage spécifiée par textRange  
  
 `textRange`  
 Plage de texte à laquelle cette modification s’applique.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la méthode réussit, elle retourne la valeur TRUE. Sinon, elle retourne FALSE  
  
##  <a name="setlocalename"></a>  CD2DTextLayout::SetLocaleName  
 Définit le nom de paramètres régionaux pour le texte dans une plage de texte spécifiée  
  
```  
BOOL SetLocaleName(
    LPCWSTR pwzLocaleName,  
    DWRITE_TEXT_RANGE textRange);
```  
  
### <a name="parameters"></a>Paramètres  
 `pwzLocaleName`  
 Une chaîne de nom se terminant par null de paramètres régionaux  
  
 `textRange`  
 Plage de texte à laquelle cette modification s’applique.  
  
### <a name="return-value"></a>Valeur de retour  
 Si la méthode réussit, elle retourne la valeur TRUE. Sinon, elle retourne FALSE  
  
## <a name="see-also"></a>Voir aussi  
 [Classes](../../mfc/reference/mfc-classes.md)
