---
title: CWinFormsControl, classe
ms.date: 11/04/2016
f1_keywords:
- CWinFormsControl
- AFXWINFORMS/CWinFormsControl
- AFXWINFORMS/CWinFormsControl::CWinFormsControl
- AFXWINFORMS/CWinFormsControl::CreateManagedControl
- AFXWINFORMS/CWinFormsControl::GetControl
- AFXWINFORMS/CWinFormsControl::GetControlHandle
helpviewer_keywords:
- CWinFormsControl [MFC], CWinFormsControl
- CWinFormsControl [MFC], CreateManagedControl
- CWinFormsControl [MFC], GetControl
- CWinFormsControl [MFC], GetControlHandle
ms.assetid: 6406dd7b-fb89-4a18-ac3a-c010d6b6289a
ms.openlocfilehash: c91f50be1ea30efac81ff67c43633bedd7b0ca03
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377178"
---
# <a name="cwinformscontrol-class"></a>CWinFormsControl, classe

Fournit les fonctionnalités de base pour l'hébergement d'un contrôle Windows Forms.

## <a name="syntax"></a>Syntaxe

```
template<class TManagedControl>
class CWinFormsControl : public CWnd
```

#### <a name="parameters"></a>Paramètres

*TManagedControl*<br/>
Un contrôle .NET Framework Windows Forms à afficher dans l’application MFC.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CWinFormsControl::CWinFormsControl](#cwinformscontrol)|Construit un objet d’emballage de contrôle MFC Windows Forms.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CWinFormsControl::CreateManagedControl](#createmanagedcontrol)|Crée un contrôle des formulaires Windows dans un conteneur MFC.|
|[CWinFormsControl::GetControl](#getcontrol)|Récupère un pointeur sur le contrôle des formulaires Windows.|
|[CWinFormsControl::GetControlHandle](#getcontrolhandle)|Récupère une poignée au contrôle des formulaires Windows.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CWinFormsControl::opérateur -&gt;](#operator_-_gt)|Remplace [CWinFormsControl::GetControl](#getcontrol) dans les expressions.|
|[CWinFormsControl::opérateur TManagedControl](#operator_tmanagedcontrol)|Lance un type comme pointeur vers un contrôle Windows Forms.|

## <a name="remarks"></a>Notes

La `CWinFormsControl` classe fournit la fonctionnalité de base pour l’hébergement d’un contrôle Windows Forms.

Pour plus d’informations sur l’utilisation des formulaires Windows, voir [à l’aide d’un contrôle de l’utilisateur de formulaire Windows dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

Votre code MFC ne doit pas mettre `m_hWnd`en cache les poignées de fenêtre (généralement stockées dans ). Certaines propriétés de contrôle de Windows `Window` Forms exigent que `DestroyWindow` `CreateWindow`le Win32 sous-jacent soit détruit et recréé à l’aide et . L’implémentation MFC `Destroy` `Create` Windows Forms gère les `m_hWnd` contrôles et les événements pour mettre à jour le membre.

> [!NOTE]
> L’intégration de MFC Windows Forms ne fonctionne que dans les projets qui se lient dynamiquement à MFC (dans lequel AFXDLL est défini).

## <a name="requirements"></a>Spécifications

**En-tête:** afxwinforms.h

## <a name="cwinformscontrolcreatemanagedcontrol"></a><a name="createmanagedcontrol"></a>CWinFormsControl::CreateManagedControl

Crée un contrôle des formulaires Windows dans un conteneur MFC.

```
inline BOOL CreateManagedControl(
    System::Type^ pType,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    int nID)
inline BOOL CreateManagedControl(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    int nID);

inline BOOL CreateManagedControl(
    DWORD dwStyle,
    int nPlaceHolderID,
    CWnd* pParentWnd);

inline BOOL CreateManagedControl(
    typename TManagedControl^ pControl,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    int nID);
```

### <a name="parameters"></a>Paramètres

*pType (en)*<br/>
Le type de données du contrôle à créer. Doit être un type de données [type.](/dotnet/api/system.type)

*dwStyle (en)*<br/>
Le style de fenêtre à appliquer au contrôle. Spécifier une combinaison de styles de [fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles). Actuellement, seuls les styles suivants sont pris en charge : WS_TABSTOP, WS_VISIBLE, WS_DISABLED et WS_GROUP.

*Rect*<br/>
Une [structure RECT](/windows/win32/api/windef/ns-windef-rect) qui définit les coordonnées des coins supérieurs et inférieurs à droite du contrôle (première surcharge seulement).

*nPlaceHolderID (en)*<br/>
La poignée du contrôle statique du support de place placé dans l’éditeur de ressources. Le nouveau contrôle Windows Forms remplace le contrôle statique, en supposant sa position, z-ordre, et les styles (deuxième surcharge seulement).

*pParentWnd*<br/>
Pointeur vers la fenêtre parente.

*nID*<br/>
Le numéro d’identification des ressources à attribuer au contrôle nouvellement créé.

*pControl*<br/>
Un exemple de contrôle des formulaires Windows à associer à [l’objet CWinFormsControl](../../mfc/reference/cwinformscontrol-class.md) (quatrième surcharge seulement).

### <a name="return-value"></a>Valeur de retour

En cas de succès, retourne une valeur non zéro. En cas d’échec, retourne zéro.

### <a name="remarks"></a>Notes

Cette méthode permet d’instantanéise un contrôle .NET Framework Windows Forms dans un conteneur MFC.

La première surcharge de la méthode accepte un *pType* de type de données cadre .NET afin que MFC puisse instantané un nouvel objet de ce type. *pType* doit être un type de données [type.](/dotnet/api/system.type)

La deuxième surcharge de la méthode crée un `TManagedControl` contrôle windows `CWinFormsControl` Forms basé sur le paramètre du modèle de la classe. La taille et la position du `RECT` contrôle sont basées sur la structure transmise à la méthode. Seul *dwStyle* compte pour les styles.

La troisième surcharge de la méthode crée un contrôle windows Forms qui remplace un contrôle statique, le détruisant et assumant sa position, z-ordre, et les styles. Le contrôle statique ne sert que de placeholder pour le contrôle des formulaires Windows. Lors de la création du contrôle, cette surcharge combine les styles de *dwStyle* avec les styles de ressources du contrôle statique.

La quatrième surcharge de la méthode vous permet de passer dans un *pControl* de contrôle Windows Forms déjà instantané que MFC enveloppera. Il doit être du même `TManagedControl` type que `CWinFormsControl` le paramètre de modèle de la classe.

Voir [l’utilisation d’un contrôle des utilisateurs de formulaire Windows dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md) pour les échantillons sur l’utilisation des contrôles de formulaire Windows.

## <a name="cwinformscontrolcwinformscontrol"></a><a name="cwinformscontrol"></a>CWinFormsControl::CWinFormsControl

Construit un objet d’emballage de contrôle MFC Windows Forms.

```
CWinFormsControl();
```

### <a name="remarks"></a>Notes

Le contrôle des formulaires Windows est instantané lorsque vous appelez [CWinFormsControl::CreateManagedControl](#createmanagedcontrol).

## <a name="cwinformscontrolgetcontrol"></a><a name="getcontrol"></a>CWinFormsControl::GetControl

Récupère un pointeur sur le contrôle des formulaires Windows.

```
inline TManagedControl^ GetControl() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne un pointeur sur le contrôle des formulaires Windows.

### <a name="example"></a>Exemple

  Voir [CWinFormsControl::CreateManagedControl](#createmanagedcontrol).

## <a name="cwinformscontrolgetcontrolhandle"></a><a name="getcontrolhandle"></a>CWinFormsControl::GetControlHandle

Récupère une poignée au contrôle des formulaires Windows.

```
inline HWND GetControlHandle() const;
```

### <a name="return-value"></a>Valeur de retour

Retourne une poignée au contrôle des formulaires Windows.

### <a name="remarks"></a>Notes

`GetControlHandle`est une méthode d’aide qui renvoie la poignée de fenêtre stockée dans les propriétés de contrôle cadre .NET. La valeur de poignée de fenêtre est copiée à [CWnd: ::m_hWnd](../../mfc/reference/cwnd-class.md#m_hwnd) pendant l’appel à [CWnd::Attach](../../mfc/reference/cwnd-class.md#attach).

## <a name="cwinformscontroloperator--gt"></a><a name="operator_-_gt"></a>CWinFormsControl::opérateur -&gt;

Remplace [CWinFormsControl::GetControl](#getcontrol) dans les expressions.

```
inline TManagedControl^  operator->() const;
```

### <a name="remarks"></a>Notes

Cet opérateur fournit une syntaxe pratique qui remplace dans les `GetControl` expressions.

Pour plus d’informations sur les formulaires Windows, voir [à l’aide d’un contrôle de l’utilisateur de formulaire Windows dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="cwinformscontroloperator-tmanagedcontrol"></a><a name="operator_tmanagedcontrol"></a>CWinFormsControl::opérateur TManagedControl

Lance un type comme pointeur vers un contrôle Windows Forms.

```
inline operator TManagedControl^() const;
```

### <a name="remarks"></a>Notes

Cet opérateur `CWinFormsControl<TManagedControl>` passe à des fonctions qui acceptent un pointeur à un contrôle windows Forms.

## <a name="see-also"></a>Voir aussi

[CWinFormsDialog, classe](../../mfc/reference/cwinformsdialog-class.md)<br/>
[CWinFormsView, classe](../../mfc/reference/cwinformsview-class.md)
