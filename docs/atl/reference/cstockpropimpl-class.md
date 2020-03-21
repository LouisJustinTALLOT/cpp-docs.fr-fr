---
title: CStockPropImpl, classe
ms.date: 05/06/2019
f1_keywords:
- CStockPropImpl
- ATLCTL/ATL::CStockPropImpl
- ATLCTL/ATL::get_Appearance
- ATLCTL/ATL::get_AutoSize
- ATLCTL/ATL::get_BackColor
- ATLCTL/ATL::get_BackStyle
- ATLCTL/ATL::get_BorderColor
- ATLCTL/ATL::get_BorderStyle
- ATLCTL/ATL::get_BorderVisible
- ATLCTL/ATL::get_BorderWidth
- ATLCTL/ATL::get_Caption
- ATLCTL/ATL::get_DrawMode
- ATLCTL/ATL::get_DrawStyle
- ATLCTL/ATL::get_DrawWidth
- ATLCTL/ATL::get_Enabled
- ATLCTL/ATL::get_FillColor
- ATLCTL/ATL::get_FillStyle
- ATLCTL/ATL::get_Font
- ATLCTL/ATL::get_ForeColor
- ATLCTL/ATL::get_HWND
- ATLCTL/ATL::get_MouseIcon
- ATLCTL/ATL::get_MousePointer
- ATLCTL/ATL::get_Picture
- ATLCTL/ATL::get_ReadyState
- ATLCTL/ATL::get_TabStop
- ATLCTL/ATL::get_Text
- ATLCTL/ATL::getvalid
- ATLCTL/ATL::get_Window
- ATLCTL/ATL::put_Appearance
- ATLCTL/ATL::put_AutoSize
- ATLCTL/ATL::put_BackColor
- ATLCTL/ATL::put_BackStyle
- ATLCTL/ATL::put_BorderColor
- ATLCTL/ATL::put_BorderStyle
- ATLCTL/ATL::put_BorderVisible
- ATLCTL/ATL::put_BorderWidth
- ATLCTL/ATL::put_Caption
- ATLCTL/ATL::put_DrawMode
- ATLCTL/ATL::put_DrawStyle
- ATLCTL/ATL::put_DrawWidth
- ATLCTL/ATL::put_Enabled
- ATLCTL/ATL::put_FillColor
- ATLCTL/ATL::put_FillStyle
- ATLCTL/ATL::put_Font
- ATLCTL/ATL::put_ForeColor
- ATLCTL/ATL::put_HWND
- ATLCTL/ATL::put_MouseIcon
- ATLCTL/ATL::put_MousePointer
- ATLCTL/ATL::put_Picture
- ATLCTL/ATL::put_ReadyState
- ATLCTL/ATL::put_TabStop
- ATLCTL/ATL::put_Text
- ATLCTL/ATL::putvalid
- ATLCTL/ATL::put_Window
- ATLCTL/ATL::putref_Font
- ATLCTL/ATL::putref_MouseIcon
- ATLCTL/ATL::putref_Picture
helpviewer_keywords:
- CStockPropImpl class
- controls [ATL], stock properties
- stock properties, ATL controls
ms.assetid: 45f11d7d-6580-4a0e-872d-3bc8b836cfda
ms.openlocfilehash: bc349137661d7026e48688f8ef510958de270280
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075220"
---
# <a name="cstockpropimpl-class"></a>CStockPropImpl, classe

Cette classe fournit des méthodes pour la prise en charge des valeurs de propriété stock.

> [!IMPORTANT]
> Cette classe et ses membres ne peuvent pas être utilisés dans les applications qui s’exécutent dans le Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <
    class T,
    class InterfaceName,
    const IID* piid = &_ATL_IIDOF(InterfaceName),
    const GUID* plibid = &CComModule::m_libid,
    WORD wMajor = 1,
    WORD wMinor = 0,
    class tihclass = CcomTypeInfoHolder>
class ATL_NO_VTABLE CStockPropImpl :
    public IDispatchImpl<InterfaceName, piid, plibid, wMajor, wMinor, tihclass>
```

#### <a name="parameters"></a>Paramètres

*T*<br/>
Classe qui implémente le contrôle et qui dérive de `CStockPropImpl`.

*InterfaceName*<br/>
Interface double exposant les propriétés stock.

*piid*<br/>
Pointeur vers l’IID de `InterfaceName`.

*plibid*<br/>
Pointeur vers le LIBID de la bibliothèque de types contenant la définition de `InterfaceName`.

*wMajor*<br/>
Version principale de la bibliothèque de types. La valeur par défaut est 1.

*wMinor*<br/>
Version secondaire de la bibliothèque de types. La valeur par défaut est 0.

*tihclass*<br/>
Classe utilisée pour gérer les informations de type pour *T*. La valeur par défaut est `CComTypeInfoHolder`.

## <a name="members"></a>Membres

### <a name="public-methods"></a>M&#233;thodes publiques

|||
|-|-|
|[get_Appearance](#get_appearance)|Appelez cette méthode pour obtenir le style de peinture utilisé par le contrôle, par exemple plat ou 3D.|
|[get_AutoSize](#get_autosize)|Appelez cette méthode pour recevoir l’état de l’indicateur qui indique si le contrôle ne peut pas être d’une autre taille.|
|[get_BackColor](#get_backcolor)|Appelez cette méthode pour récupérer la couleur d’arrière-plan du contrôle.|
|[get_BackStyle](#get_backstyle)|Appelez cette méthode pour faire en sorte que le style d’arrière-plan du contrôle soit transparent ou opaque.|
|[get_BorderColor](#get_bordercolor)|Appelez cette méthode pour récupérer la couleur de bordure du contrôle.|
|[get_BorderStyle](#get_borderstyle)|Appelez cette méthode pour récupérer le style de bordure du contrôle.|
|[get_BorderVisible](#get_bordervisible)|Appelez cette méthode pour recevoir l’état de l’indicateur qui indique si la bordure du contrôle est visible ou non.|
|[get_BorderWidth](#get_borderwidth)|Appelez cette méthode pour atteindre la largeur (en pixels) de la bordure du contrôle.|
|[get_Caption](#get_caption)|Appelez cette méthode pour récupérer le texte spécifié dans la légende d’un objet.|
|[get_DrawMode](#get_drawmode)|Appelez cette méthode pour obtenir le mode dessin du contrôle, par exemple XOR plume ou inverser les couleurs.|
|[get_DrawStyle](#get_drawstyle)|Appelez cette méthode pour obtenir le style de dessin du contrôle, par exemple, plein, en pointillés ou en pointillés.|
|[get_DrawWidth](#get_drawwidth)|Appelez cette méthode pour récupérer la largeur de dessin (en pixels) utilisée par les méthodes de dessin du contrôle.|
|[get_Enabled](#get_enabled)|Appelez cette méthode pour recevoir l’état de l’indicateur qui indique si le contrôle est activé.|
|[get_FillColor](#get_fillcolor)|Appelez cette méthode pour récupérer la couleur de remplissage du contrôle.|
|[get_FillStyle](#get_fillstyle)|Appelez cette méthode pour obtenir le style de remplissage du contrôle, par exemple, Uni, transparent ou à hachurage croisée.|
|[get_Font](#get_font)|Appelez cette méthode pour obtenir un pointeur vers les propriétés de police du contrôle.|
|[get_ForeColor](#get_forecolor)|Appelez cette méthode pour récupérer la couleur de premier plan du contrôle.|
|[get_HWND](#get_hwnd)|Appelez cette méthode pour recevoir le handle de fenêtre associé au contrôle.|
|[get_MouseIcon](#get_mouseicon)|Appelez cette méthode pour récupérer les propriétés d’image du graphique (icône, bitmap ou métafichier) à afficher lorsque la souris se trouve sur le contrôle.|
|[get_MousePointer](#get_mousepointer)|Appelez cette méthode pour obtenir le type de pointeur de souris qui s’affiche lorsque la souris se trouve sur le contrôle, par exemple, Arrow, Cross ou HourGlass.|
|[get_Picture](#get_picture)|Appelez cette méthode pour obtenir un pointeur vers les propriétés d’image d’un graphique (icône, bitmap ou métafichier) à afficher.|
|[get_ReadyState](#get_readystate)|Appelez cette méthode pour obtenir l’état prêt du contrôle, par exemple le chargement ou le chargement.|
|[get_TabStop](#get_tabstop)|Appelez cette méthode pour obtenir l’indicateur qui signale si le contrôle est un taquet de tabulation.|
|[get_Text](#get_text)|Appelez cette méthode pour récupérer le texte qui est affiché avec le contrôle.|
|[getvalid](#get_valid)|Appelez cette méthode pour recevoir l’état de l’indicateur qui indique si le contrôle est valide ou non.|
|[get_Window](#get_window)|Appelez cette méthode pour recevoir le handle de fenêtre associé au contrôle. Identique à [CStockPropImpl :: get_HWND](#get_hwnd).|
|[put_Appearance](#put_appearance)|Appelez cette méthode pour définir le style de peinture utilisé par le contrôle, par exemple Flat ou 3D.|
|[put_AutoSize](#put_autosize)|Appelez cette méthode pour définir la valeur de l’indicateur qui indique si le contrôle ne peut pas être d’une autre taille.|
|[put_BackColor](#put_backcolor)|Appelez cette méthode pour définir la couleur d’arrière-plan du contrôle.|
|[put_BackStyle](#put_backstyle)|Appelez cette méthode pour définir le style d’arrière-plan du contrôle.|
|[put_BorderColor](#put_bordercolor)|Appelez cette méthode pour définir la couleur de bordure du contrôle.|
|[put_BorderStyle](#put_borderstyle)|Appelez cette méthode pour définir le style de bordure du contrôle.|
|[put_BorderVisible](#put_bordervisible)|Appelez cette méthode pour définir la valeur de l’indicateur qui indique si la bordure du contrôle est visible ou non.|
|[put_BorderWidth](#put_borderwidth)|Appelez cette méthode pour définir la largeur de la bordure du contrôle.|
|[put_Caption](#put_caption)|Appelez cette méthode pour définir le texte à afficher avec le contrôle.|
|[put_DrawMode](#put_drawmode)|Appelez cette méthode pour définir le mode de dessin du contrôle, par exemple XOR PEN ou inverser les couleurs.|
|[put_DrawStyle](#put_drawstyle)|Appelez cette méthode pour définir le style de dessin du contrôle, par exemple, plein, en pointillés ou en pointillés.|
|[put_DrawWidth](#put_drawwidth)|Appelez cette méthode pour définir la largeur (en pixels) utilisée par les méthodes de dessin du contrôle.|
|[put_Enabled](#put_enabled)|Appelez cette méthode pour définir l’indicateur qui signale si le contrôle est activé.|
|[put_FillColor](#put_fillcolor)|Appelez cette méthode pour définir la couleur de remplissage du contrôle.|
|[put_FillStyle](#put_fillstyle)|Appelez cette méthode pour définir le style de remplissage du contrôle, par exemple, Uni, transparent ou à hachurage croisée.|
|[put_Font](#put_font)|Appelez cette méthode pour définir les propriétés de police du contrôle.|
|[put_ForeColor](#put_forecolor)|Appelez cette méthode pour définir la couleur de premier plan du contrôle.|
|[put_HWND](#put_hwnd)|Cette méthode retourne E_FAIL.|
|[put_MouseIcon](#put_mouseicon)|Appelez cette méthode pour définir les propriétés d’image du graphique (icône, bitmap ou métafichier) à afficher lorsque la souris se trouve sur le contrôle.|
|[put_MousePointer](#put_mousepointer)|Appelez cette méthode pour définir le type de pointeur de la souris qui s’affiche lorsque la souris se trouve sur le contrôle, par exemple, Arrow, Cross ou HourGlass.|
|[put_Picture](#put_picture)|Appelez cette méthode pour définir l’affichage des propriétés de l’image d’un graphique (icône, bitmap ou métafichier).|
|[put_ReadyState](#put_readystate)|Appelez cette méthode pour définir l’état prêt du contrôle, par exemple le chargement ou le chargement.|
|[put_TabStop](#put_tabstop)|Appelez cette méthode pour définir la valeur de l’indicateur qui indique si le contrôle est un taquet de tabulation.|
|[put_Text](#put_text)|Appelez cette méthode pour définir le texte qui est affiché avec le contrôle.|
|[putvalid](#put_valid)|Appelez cette méthode pour définir l’indicateur qui signale si le contrôle est valide ou non.|
|[put_Window](#put_window)|Cette méthode appelle [CStockPropImpl ::p ut_HWND](#put_hwnd), qui retourne E_FAIL.|
|[putref_Font](#putref_font)|Appelez cette méthode pour définir les propriétés de police du contrôle, avec un nombre de références.|
|[putref_MouseIcon](#putref_mouseicon)|Appelez cette méthode pour définir les propriétés d’image du graphique (icône, bitmap ou métafichier) à afficher lorsque la souris se trouve sur le contrôle, avec un nombre de références.|
|[putref_Picture](#putref_picture)|Appelez cette méthode pour définir les propriétés d’image d’un graphique (icône, bitmap ou métafichier) à afficher, avec un décompte de références.|

## <a name="remarks"></a>Notes

`CStockPropImpl` fournit des méthodes **put** et **obtenir** pour chaque propriété stock. Ces méthodes fournissent le code nécessaire pour définir ou obtenir le membre de données associé à chaque propriété, et pour notifier et synchroniser avec le conteneur lorsqu’une propriété change.

Visual Studio prend en charge les propriétés stock par le biais de ses assistants. Pour plus d’informations sur l’ajout de propriétés stock à un contrôle, consultez le [Didacticiel ATL](../../atl/active-template-library-atl-tutorial.md).

Pour la compatibilité descendante, `CStockPropImpl` expose également des méthodes `get_Window` et `put_Window` qui appellent simplement `get_HWND` et `put_HWND`, respectivement. L’implémentation par défaut de `put_HWND` Retourne E_FAIL puisque HWND doit être une propriété en lecture seule.

Les propriétés suivantes ont également une implémentation de **PutRef** :

- Police

- MouseIcon

- Photo

Les trois mêmes propriétés stock nécessitent que leurs données membres correspondantes soient de type `CComPtr` ou d’une autre classe qui fournit le décompte de références d’interface correct au moyen de l’opérateur d’assignation.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

`T`

[IDispatchImpl](../../atl/reference/idispatchimpl-class.md)

`CStockPropImpl`

## <a name="requirements"></a>Spécifications

**En-tête :** atlctl. h

##  <a name="cstockpropimplget_appearance"></a><a name="get_appearance"></a>CStockPropImpl :: get_Appearance

Appelez cette méthode pour obtenir le style de peinture utilisé par le contrôle, par exemple plat ou 3D.

```
HRESULT STDMETHODCALLTYPE get_Appearance(SHORT pnAppearance);
```

### <a name="parameters"></a>Paramètres

*pnAppearance*<br/>
Variable qui reçoit le style de peinture du contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplget_autosize"></a><a name="get_autosize"></a>CStockPropImpl :: get_AutoSize

Appelez cette méthode pour recevoir l’état de l’indicateur qui indique si le contrôle ne peut pas être d’une autre taille.

```
HRESULT STDMETHODCALLTYPE get_Autosize(VARIANT_BOOL* pbAutoSize);
```

### <a name="parameters"></a>Paramètres

*pbAutoSize*<br/>
Variable qui reçoit l’état de l’indicateur. TRUE indique que le contrôle ne peut pas être d’une autre taille.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplget_backcolor"></a><a name="get_backcolor"></a>CStockPropImpl :: get_BackColor

Appelez cette méthode pour récupérer la couleur d’arrière-plan du contrôle.

```
HRESULT STDMETHODCALLTYPE get_BackColor(OLE_COLOR* pclrBackColor);
```

### <a name="parameters"></a>Paramètres

*pclrBackColor*<br/>
Variable qui reçoit la couleur d’arrière-plan du contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplget_backstyle"></a><a name="get_backstyle"></a>CStockPropImpl :: get_BackStyle

Appelez cette méthode pour faire en sorte que le style d’arrière-plan du contrôle soit transparent ou opaque.

```
HRESULT STDMETHODCALLTYPE get_BackStyle(LONG* pnBackStyle);
```

### <a name="parameters"></a>Paramètres

*pnBackStyle*<br/>
Variable qui reçoit le style d’arrière-plan du contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplget_bordercolor"></a><a name="get_bordercolor"></a>CStockPropImpl :: get_BorderColor

Appelez cette méthode pour récupérer la couleur de bordure du contrôle.

```
HRESULT STDMETHODCALLTYPE get_BorderColor(OLE_COLOR* pclrBorderColor);
```

### <a name="parameters"></a>Paramètres

*pclrBorderColor*<br/>
Variable qui reçoit la couleur de bordure du contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplget_borderstyle"></a><a name="get_borderstyle"></a>CStockPropImpl :: get_BorderStyle

Appelez cette méthode pour récupérer le style de bordure du contrôle.

```
HRESULT STDMETHODCALLTYPE get_BorderStyle(LONG* pnBorderStyle);
```

### <a name="parameters"></a>Paramètres

*pnBorderStyle*<br/>
Variable qui reçoit le style de bordure du contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplget_bordervisible"></a><a name="get_bordervisible"></a>CStockPropImpl :: get_BorderVisible

Appelez cette méthode pour recevoir l’état de l’indicateur qui indique si la bordure du contrôle est visible ou non.

```
HRESULT STDMETHODCALLTYPE get_BorderVisible(VARIANT_BOOL* pbBorderVisible);
```

### <a name="parameters"></a>Paramètres

*pbBorderVisible*<br/>
Variable qui reçoit l’état de l’indicateur. TRUE indique que la bordure du contrôle est visible.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplget_borderwidth"></a><a name="get_borderwidth"></a>CStockPropImpl :: get_BorderWidth

Appelez cette méthode pour atteindre la largeur de la bordure du contrôle.

```
HRESULT STDMETHODCALLTYPE get_BorderWidth(LONG* pnBorderWidth);
```

### <a name="parameters"></a>Paramètres

*pnBorderWidth*<br/>
Variable qui reçoit la largeur de bordure du contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplget_caption"></a><a name="get_caption"></a>CStockPropImpl :: get_Caption

Appelez cette méthode pour récupérer le texte spécifié dans la légende d’un objet.

```
HRESULT STDMETHODCALLTYPE get_Caption(BSTR* pbstrCaption);
```

### <a name="parameters"></a>Paramètres

*pbstrCaption*<br/>
Texte à afficher avec le contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplget_drawmode"></a><a name="get_drawmode"></a>CStockPropImpl :: get_DrawMode

Appelez cette méthode pour obtenir le mode dessin du contrôle, par exemple XOR plume ou inverser les couleurs.

```
HRESULT STDMETHODCALLTYPE get_DrawMode(LONG* pnDrawMode);
```

### <a name="parameters"></a>Paramètres

*pnDrawMode*<br/>
Variable qui reçoit le mode dessin du contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplget_drawstyle"></a><a name="get_drawstyle"></a>CStockPropImpl :: get_DrawStyle

Appelez cette méthode pour obtenir le style de dessin du contrôle, par exemple, plein, en pointillés ou en pointillés.

```
HRESULT STDMETHODCALLTYPE get_DrawStyle(LONG* pnDrawStyle);
```

### <a name="parameters"></a>Paramètres

*pnDrawStyle*<br/>
Variable qui reçoit le style de dessin du contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplget_drawwidth"></a><a name="get_drawwidth"></a>CStockPropImpl :: get_DrawWidth

Appelez cette méthode pour récupérer la largeur de dessin (en pixels) utilisée par les méthodes de dessin du contrôle.

```
HRESULT STDMETHODCALLTYPE get_DrawWidth(LONG* pnDrawWidth);
```

### <a name="parameters"></a>Paramètres

*pnDrawWidth*<br/>
Variable qui reçoit la valeur de largeur du contrôle, en pixels.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplget_enabled"></a><a name="get_enabled"></a>CStockPropImpl :: get_Enabled

Appelez cette méthode pour recevoir l’état de l’indicateur qui indique si le contrôle est activé.

```
HRESULT STDMETHODCALLTYPE get_Enabled(VARIANT_BOOL* pbEnabled);
```

### <a name="parameters"></a>Paramètres

*pbEnabled*<br/>
Variable qui reçoit l’état de l’indicateur. TRUE indique que le contrôle est activé.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplget_fillcolor"></a><a name="get_fillcolor"></a>CStockPropImpl :: get_FillColor

Appelez cette méthode pour récupérer la couleur de remplissage du contrôle.

```
HRESULT STDMETHODCALLTYPE get_FillColor(OLE_COLOR* pclrFillColor);
```

### <a name="parameters"></a>Paramètres

*pclrFillColor*<br/>
Variable qui reçoit la couleur de remplissage du contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplget_fillstyle"></a><a name="get_fillstyle"></a>CStockPropImpl :: get_FillStyle

Appelez cette méthode pour obtenir le style de remplissage du contrôle, par exemple, Uni, transparent ou hachurée.

```
HRESULT STDMETHODCALLTYPE get_FillStyle(LONG* pnFillStyle);
```

### <a name="parameters"></a>Paramètres

*pnFillStyle*<br/>
Variable qui reçoit le style de remplissage du contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplget_font"></a><a name="get_font"></a>CStockPropImpl :: get_Font

Appelez cette méthode pour obtenir un pointeur vers les propriétés de police du contrôle.

```
HRESULT STDMETHODCALLTYPE get_Font(IFontDisp** ppFont);
```

### <a name="parameters"></a>Paramètres

*ppFont*<br/>
Variable qui reçoit un pointeur vers les propriétés de police du contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplget_forecolor"></a><a name="get_forecolor"></a>CStockPropImpl :: get_ForeColor

Appelez cette méthode pour récupérer la couleur de premier plan du contrôle.

```
HRESULT STDMETHODCALLTYPE get_ForeColor(OLE_COLOR* pclrForeColor);
```

### <a name="parameters"></a>Paramètres

*pclrForeColor*<br/>
Variable qui reçoit la couleur de premier plan des contrôles.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplget_hwnd"></a><a name="get_hwnd"></a>CStockPropImpl :: get_HWND

Appelez cette méthode pour recevoir le handle de fenêtre associé au contrôle.

```
HRESULT STDMETHODCALLTYPE get_HWND(LONG_PTR* phWnd);
```

### <a name="parameters"></a>Paramètres

*phWnd*<br/>
Handle de fenêtre associé au contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplget_mouseicon"></a><a name="get_mouseicon"></a>CStockPropImpl :: get_MouseIcon

Appelez cette méthode pour récupérer les propriétés d’image du graphique (icône, bitmap ou métafichier) à afficher lorsque la souris se trouve sur le contrôle.

```
HRESULT STDMETHODCALLTYPE get_MouseIcon(IPictureDisp** ppPicture);
```

### <a name="parameters"></a>Paramètres

*ppPicture*<br/>
Variable qui reçoit un pointeur vers les propriétés image du graphique.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplget_mousepointer"></a><a name="get_mousepointer"></a>CStockPropImpl :: get_MousePointer

Appelez cette méthode pour obtenir le type de pointeur de souris qui s’affiche lorsque la souris se trouve sur le contrôle, par exemple, Arrow, Cross ou HourGlass.

```
HRESULT STDMETHODCALLTYPE get_MousePointer(LONG* pnMousePointer);
```

### <a name="parameters"></a>Paramètres

*pnMousePointer*<br/>
Variable qui reçoit le type de pointeur de la souris.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplget_picture"></a><a name="get_picture"></a>CStockPropImpl :: get_Picture

Appelez cette méthode pour obtenir un pointeur vers les propriétés d’image d’un graphique (icône, bitmap ou métafichier) à afficher.

```
HRESULT STDMETHODCALLTYPE get_Picture(IPictureDisp** ppPicture);
```

### <a name="parameters"></a>Paramètres

*ppPicture*<br/>
Variable qui reçoit un pointeur vers les propriétés de l’image. Pour plus d’informations, consultez [IPictureDisp](/windows/win32/api/ocidl/nn-ocidl-ipicturedisp) .

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplget_readystate"></a><a name="get_readystate"></a>CStockPropImpl :: get_ReadyState

Appelez cette méthode pour obtenir l’état prêt du contrôle, par exemple le chargement ou le chargement.

```
HRESULT STDMETHODCALLTYPE get_ReadyState(LONG* pnReadyState);
```

### <a name="parameters"></a>Paramètres

*pnReadyState*<br/>
Variable qui reçoit l’état prêt du contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplget_tabstop"></a><a name="get_tabstop"></a>CStockPropImpl :: get_TabStop

Appelez cette méthode pour obtenir l’état de l’indicateur qui indique si le contrôle est un taquet de tabulation.

```
HRESULT STDMETHODCALLTYPE get_TabStop(VARIANT_BOOL* pbTabStop);
```

### <a name="parameters"></a>Paramètres

*pbTabStop*<br/>
Variable qui reçoit l’état de l’indicateur. TRUE indique que le contrôle est un taquet de tabulation.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplget_text"></a><a name="get_text"></a>CStockPropImpl :: get_Text

Appelez cette méthode pour récupérer le texte qui est affiché avec le contrôle.

```
HRESULT STDMETHODCALLTYPE get_Text(BSTR* pbstrText);
```

### <a name="parameters"></a>Paramètres

*pbstrText*<br/>
Texte affiché avec le contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplgetvalid"></a><a name="get_valid"></a>CStockPropImpl::getvalid

Appelez cette méthode pour recevoir l’état de l’indicateur qui indique si le contrôle est valide ou non.

```
HRESULT STDMETHODCALLTYPE getvalid(VARIANT_BOOL* pbValid);
```

### <a name="parameters"></a>Paramètres

*pbValid*<br/>
Variable qui reçoit l’état de l’indicateur. TRUE indique que le contrôle est valide.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplget_window"></a><a name="get_window"></a>CStockPropImpl :: get_Window

Appelez cette méthode pour recevoir le handle de fenêtre associé au contrôle. Identique à [CStockPropImpl :: get_HWND](#get_hwnd).

```
HRESULT STDMETHODCALLTYPE get_Window(LONG_PTR* phWnd);
```

### <a name="parameters"></a>Paramètres

*phWnd*<br/>
Handle de fenêtre associé au contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplput_appearance"></a><a name="put_appearance"></a>CStockPropImpl ::p ut_Appearance

Appelez cette méthode pour définir le style de peinture utilisé par le contrôle, par exemple Flat ou 3D.

```
HRESULT STDMETHODCALLTYPE put_Appearance(SHORT nAppearance);
```

### <a name="parameters"></a>Paramètres

*nAppearance*<br/>
Nouveau style de peinture à utiliser par le contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplput_autosize"></a><a name="put_autosize"></a>CStockPropImpl ::p ut_AutoSize

Appelez cette méthode pour définir la valeur de l’indicateur qui indique si le contrôle ne peut pas être d’une autre taille.

```
HRESULT STDMETHODCALLTYPE put_AutoSize(VARIANT_BOOL bAutoSize,);
```

### <a name="parameters"></a>Paramètres

*bAutoSize*<br/>
TRUE si le contrôle ne peut pas être d’une autre taille.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplput_backcolor"></a><a name="put_backcolor"></a>CStockPropImpl ::p ut_BackColor

Appelez cette méthode pour définir la couleur d’arrière-plan du contrôle.

```
HRESULT STDMETHODCALLTYPE put_BackColor(OLE_COLOR clrBackColor);
```

### <a name="parameters"></a>Paramètres

*clrBackColor*<br/>
Nouvelle couleur d’arrière-plan du contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplput_backstyle"></a><a name="put_backstyle"></a>CStockPropImpl ::p ut_BackStyle

Appelez cette méthode pour définir le style d’arrière-plan du contrôle.

```
HRESULT STDMETHODCALLTYPE put_BackStyle(LONG nBackStyle);
```

### <a name="parameters"></a>Paramètres

*nBackStyle*<br/>
Nouveau style d’arrière-plan du contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplput_bordercolor"></a><a name="put_bordercolor"></a>CStockPropImpl ::p ut_BorderColor

Appelez cette méthode pour définir la couleur de bordure du contrôle.

```
HRESULT STDMETHODCALLTYPE put_BorderColor(OLE_COLOR clrBorderColor);
```

### <a name="parameters"></a>Paramètres

*clrBorderColor*<br/>
Nouvelle couleur de bordure. Le type de données OLE_COLOR est représenté en interne sous la forme d’un entier long de 32 bits.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplput_borderstyle"></a><a name="put_borderstyle"></a>CStockPropImpl ::p ut_BorderStyle

Appelez cette méthode pour définir le style de bordure du contrôle.

```
HRESULT STDMETHODCALLTYPE put_BorderStyle(LONG nBorderStyle);
```

### <a name="parameters"></a>Paramètres

*nBorderStyle*<br/>
Nouveau style de bordure.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplput_bordervisible"></a><a name="put_bordervisible"></a>CStockPropImpl ::p ut_BorderVisible

Appelez cette méthode pour définir la valeur de l’indicateur qui indique si la bordure du contrôle est visible ou non.

```
HRESULT STDMETHODCALLTYPE put_BorderVisible(VARIANT_BOOL bBorderVisible);
```

### <a name="parameters"></a>Paramètres

*bBorderVisible*<br/>
TRUE si la bordure doit être visible.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplput_borderwidth"></a><a name="put_borderwidth"></a>CStockPropImpl ::p ut_BorderWidth

Appelez cette méthode pour définir la largeur de la bordure du contrôle.

```
HRESULT STDMETHODCALLTYPE put_BorderWidth(LONG nBorderWidth);
```

### <a name="parameters"></a>Paramètres

*nBorderWidth*<br/>
Nouvelle largeur de la bordure du contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplput_caption"></a><a name="put_caption"></a>CStockPropImpl ::p ut_Caption

Appelez cette méthode pour définir le texte à afficher avec le contrôle.

```
HRESULT STDMETHODCALLTYPE put_Caption(BSTR bstrCaption);
```

### <a name="parameters"></a>Paramètres

*bstrCaption*<br/>
Texte à afficher avec le contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplput_drawmode"></a><a name="put_drawmode"></a>CStockPropImpl ::p ut_DrawMode

Appelez cette méthode pour définir le mode de dessin du contrôle, par exemple XOR PEN ou inverser les couleurs.

```
HRESULT STDMETHODCALLTYPE put_DrawMode(LONG nDrawMode);
```

### <a name="parameters"></a>Paramètres

*nDrawMode*<br/>
Nouveau mode dessin du contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplput_drawstyle"></a><a name="put_drawstyle"></a>CStockPropImpl ::p ut_DrawStyle

Appelez cette méthode pour définir le style de dessin du contrôle, par exemple, plein, en pointillés ou en pointillés.

```
HRESULT STDMETHODCALLTYPE put_DrawStyle(LONG pnDrawStyle);
```

### <a name="parameters"></a>Paramètres

*nDrawStyle*<br/>
Nouveau style de dessin pour le contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplput_drawwidth"></a><a name="put_drawwidth"></a>CStockPropImpl ::p ut_DrawWidth

Appelez cette méthode pour définir la largeur (en pixels) utilisée par les méthodes de dessin du contrôle.

```
HRESULT STDMETHODCALLTYPE put_DrawWidth(LONG nDrawWidth);
```

### <a name="parameters"></a>Paramètres

*nDrawWidth*<br/>
Nouvelle largeur à utiliser par les méthodes de dessin du contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplput_enabled"></a><a name="put_enabled"></a>CStockPropImpl ::p ut_Enabled

Appelez cette méthode pour définir la valeur de l’indicateur qui indique si le contrôle est activé.

```
HRESULT STDMETHODCALLTYPE put_Enabled(VARIANT_BOOL bEnabled);
```

### <a name="parameters"></a>Paramètres

*bEnabled*<br/>
TRUE si le contrôle est activé.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplput_fillcolor"></a><a name="put_fillcolor"></a>CStockPropImpl ::p ut_FillColor

Appelez cette méthode pour définir la couleur de remplissage du contrôle.

```
HRESULT STDMETHODCALLTYPE put_FillColor(OLE_COLOR clrFillColor);
```

### <a name="parameters"></a>Paramètres

*clrFillColor*<br/>
Nouvelle couleur de remplissage du contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplput_fillstyle"></a><a name="put_fillstyle"></a>CStockPropImpl ::p ut_FillStyle

Appelez cette méthode pour définir le style de remplissage du contrôle, par exemple, Uni, transparent ou à hachurage croisée.

```
HRESULT STDMETHODCALLTYPE put_FillStyle(LONG nFillStyle);
```

### <a name="parameters"></a>Paramètres

*nFillStyle*<br/>
Nouveau style de remplissage du contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplput_font"></a><a name="put_font"></a>CStockPropImpl ::p ut_Font

Appelez cette méthode pour définir les propriétés de police du contrôle.

```
HRESULT STDMETHODCALLTYPE put_Font(IFontDisp* pFont);
```

### <a name="parameters"></a>Paramètres

*pFont*<br/>
Pointeur vers les propriétés de police du contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplput_forecolor"></a><a name="put_forecolor"></a>CStockPropImpl ::p ut_ForeColor

Appelez cette méthode pour définir la couleur de premier plan du contrôle.

```
HRESULT STDMETHODCALLTYPE put_ForeColor(OLE_COLOR clrForeColor);
```

### <a name="parameters"></a>Paramètres

*clrForeColor*<br/>
Nouvelle couleur de premier plan du contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplput_hwnd"></a><a name="put_hwnd"></a>CStockPropImpl ::p ut_HWND

Cette méthode retourne E_FAIL.

```
HRESULT STDMETHODCALLTYPE put_HWND(LONG_PTR /* hWnd */);
```

### <a name="parameters"></a>Paramètres

*hWnd*<br/>
Réservé.

### <a name="return-value"></a>Valeur de retour

Retourne E_FAIL.

### <a name="remarks"></a>Notes

Le handle de fenêtre est une valeur en lecture seule.

##  <a name="cstockpropimplput_mouseicon"></a><a name="put_mouseicon"></a>CStockPropImpl ::p ut_MouseIcon

Appelez cette méthode pour définir les propriétés d’image du graphique (icône, bitmap ou métafichier) à afficher lorsque la souris se trouve sur le contrôle.

```
HRESULT STDMETHODCALLTYPE put_MouseIcon(IPictureDisp* pPicture);
```

### <a name="parameters"></a>Paramètres

*pPicture*<br/>
Pointeur vers les propriétés d’image du graphique.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplput_mousepointer"></a><a name="put_mousepointer"></a>CStockPropImpl ::p ut_MousePointer

Appelez cette méthode pour définir le type de pointeur de la souris qui s’affiche lorsque la souris se trouve sur le contrôle, par exemple, Arrow, Cross ou HourGlass.

```
HRESULT STDMETHODCALLTYPE put_MousePointer(LONG nMousePointer);
```

### <a name="parameters"></a>Paramètres

*nMousePointer*<br/>
Type du pointeur de la souris.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplput_picture"></a><a name="put_picture"></a>CStockPropImpl ::p ut_Picture

Appelez cette méthode pour définir l’affichage des propriétés de l’image d’un graphique (icône, bitmap ou métafichier).

```
HRESULT STDMETHODCALLTYPE put_Picture(IPictureDisp* pPicture);
```

### <a name="parameters"></a>Paramètres

*pPicture*<br/>
Pointeur vers les propriétés de l’image. Pour plus d’informations, consultez [IPictureDisp](/windows/win32/api/ocidl/nn-ocidl-ipicturedisp) .

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplput_readystate"></a><a name="put_readystate"></a>CStockPropImpl ::p ut_ReadyState

Appelez cette méthode pour définir l’état prêt du contrôle, par exemple le chargement ou le chargement.

```
HRESULT STDMETHODCALLTYPE put_ReadyState(LONG nReadyState);
```

### <a name="parameters"></a>Paramètres

*nReadyState*<br/>
État prêt du contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplput_tabstop"></a><a name="put_tabstop"></a>CStockPropImpl ::p ut_TabStop

Appelez cette méthode pour définir l’indicateur qui signale si le contrôle est un taquet de tabulation.

```
HRESULT STDMETHODCALLTYPE put_TabStop(VARIANT_BOOL bTabStop);
```

### <a name="parameters"></a>Paramètres

*bTabStop*<br/>
TRUE si le contrôle est un taquet de tabulation.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplput_text"></a><a name="put_text"></a>CStockPropImpl ::p ut_Text

Appelez cette méthode pour définir le texte qui est affiché avec le contrôle.

```
HRESULT STDMETHODCALLTYPE put_Text(BSTR bstrText);
```

### <a name="parameters"></a>Paramètres

*bstrText*<br/>
Texte affiché avec le contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplputvalid"></a><a name="put_valid"></a>CStockPropImpl ::p utvalid

Appelez cette méthode pour définir l’indicateur qui signale si le contrôle est valide ou non.

```
HRESULT STDMETHODCALLTYPE getvalid(VARIANT_BOOL bValid);
```

### <a name="parameters"></a>Paramètres

*bValid*<br/>
TRUE si le contrôle est valide.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

##  <a name="cstockpropimplput_window"></a><a name="put_window"></a>CStockPropImpl ::p ut_Window

Cette méthode appelle [CStockPropImpl ::p ut_HWND](#put_hwnd), qui retourne E_FAIL.

```
HRESULT STDMETHODCALLTYPE put_Window(LONG_PTR hWnd);
```

### <a name="parameters"></a>Paramètres

*hWnd*<br/>
Handle de fenêtre.

### <a name="return-value"></a>Valeur de retour

Retourne E_FAIL.

### <a name="remarks"></a>Notes

Le handle de fenêtre est une valeur en lecture seule.

##  <a name="cstockpropimplputref_font"></a><a name="putref_font"></a>CStockPropImpl ::p utref_Font

Appelez cette méthode pour définir les propriétés de police du contrôle, avec un nombre de références.

```
HRESULT STDMETHODCALLTYPE putref_Font(IFontDisp* pFont);
```

### <a name="parameters"></a>Paramètres

*pFont*<br/>
Pointeur vers les propriétés de police du contrôle.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Identique à [CStockPropImpl ::p ut_Font](#put_font), mais avec un nombre de références.

##  <a name="cstockpropimplputref_mouseicon"></a><a name="putref_mouseicon"></a>CStockPropImpl ::p utref_MouseIcon

Appelez cette méthode pour définir les propriétés d’image du graphique (icône, bitmap ou métafichier) à afficher lorsque la souris se trouve sur le contrôle, avec un nombre de références.

```
HRESULT STDMETHODCALLTYPE putref_MouseIcon(IPictureDisp* pPicture);
```

### <a name="parameters"></a>Paramètres

*pPicture*<br/>
Pointeur vers les propriétés d’image du graphique.

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Identique à [CStockPropImpl ::p ut_MouseIcon](#put_mouseicon), mais avec un nombre de références.

##  <a name="cstockpropimplputref_picture"></a><a name="putref_picture"></a>CStockPropImpl ::p utref_Picture

Appelez cette méthode pour définir les propriétés d’image d’un graphique (icône, bitmap ou métafichier) à afficher, avec un décompte de références.

```
HRESULT STDMETHODCALLTYPE putref_Picture(IPictureDisp* pPicture);
```

### <a name="parameters"></a>Paramètres

*pPicture*<br/>
Pointeur vers les propriétés de l’image. Pour plus d’informations, consultez [IPictureDisp](/windows/win32/api/ocidl/nn-ocidl-ipicturedisp) .

### <a name="return-value"></a>Valeur de retour

Retourne S_OK en cas de réussite, ou un HRESULT d’erreur en cas d’échec.

### <a name="remarks"></a>Notes

Identique à [CStockPropImpl ::p ut_Picture](#put_picture), mais avec un nombre de références.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la classe](../../atl/atl-class-overview.md)<br/>
[IDispatchImpl, classe](../../atl/reference/idispatchimpl-class.md)
