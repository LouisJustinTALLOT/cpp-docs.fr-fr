---
description: 'En savoir plus sur : classe CWinFormsControl'
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
ms.openlocfilehash: 32daf5f1bf9efcd5d5b17d134dc8deaee7e32527
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318440"
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
.NET Framework Windows Forms contrôle à afficher dans l’application MFC.

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CWinFormsControl::CWinFormsControl](#cwinformscontrol)|Construit un objet de wrapper de contrôle MFC Windows Forms.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CWinFormsControl::CreateManagedControl](#createmanagedcontrol)|Crée un contrôle de Windows Forms dans un conteneur MFC.|
|[CWinFormsControl::GetControl](#getcontrol)|Récupère un pointeur désignant le contrôle de Windows Forms.|
|[CWinFormsControl::GetControlHandle](#getcontrolhandle)|Récupère un handle vers le contrôle de Windows Forms.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CWinFormsControl :: Operator-&gt;](#operator_-_gt)|Remplace [CWinFormsControl :: GetControl](#getcontrol) dans les expressions.|
|[CWinFormsControl :: Operator TManagedControl ^](#operator_tmanagedcontrol)|Effectue un cast d’un type en pointeur vers un contrôle de Windows Forms.|

## <a name="remarks"></a>Notes

La `CWinFormsControl` classe fournit les fonctionnalités de base pour l’hébergement d’un contrôle de Windows Forms.

Pour plus d’informations sur l’utilisation de Windows Forms, consultez [utilisation d’un contrôle utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

Votre code MFC ne doit pas mettre en cache des handles de fenêtre (généralement stockés dans `m_hWnd` ). Certaines propriétés de contrôle Windows Forms requièrent que le Win32 sous-jacent `Window` soit détruit et recréé à l’aide `DestroyWindow` de et de `CreateWindow` . L’implémentation de Windows Forms MFC gère `Destroy` les `Create` événements et des contrôles pour mettre à jour le `m_hWnd` membre.

> [!NOTE]
> L’intégration des Windows Forms MFC fonctionne uniquement dans les projets qui sont liés de manière dynamique aux MFC (dans lesquelles AFXDLL est défini).

## <a name="requirements"></a>Spécifications

**En-tête :** afxwinforms. h

## <a name="cwinformscontrolcreatemanagedcontrol"></a><a name="createmanagedcontrol"></a> CWinFormsControl::CreateManagedControl

Crée un contrôle de Windows Forms dans un conteneur MFC.

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

*pType*<br/>
Type de données du contrôle à créer. Doit être un type de données de [type](/dotnet/api/system.type) .

*dwStyle*<br/>
Style de fenêtre à appliquer au contrôle. Spécifiez une combinaison de [styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles). Actuellement, seuls les styles suivants sont pris en charge : WS_TABSTOP, WS_VISIBLE, WS_DISABLED et WS_GROUP.

*rectangulaire*<br/>
[Structure Rect](/windows/win32/api/windef/ns-windef-rect) qui définit les coordonnées des angles supérieur gauche et inférieur droit du contrôle (première surcharge uniquement).

*nPlaceHolderID*<br/>
Handle du contrôle de l’espace réservé statique placé dans l’éditeur de ressources. Le contrôle de Windows Forms nouvellement créé remplace le contrôle statique, en supposant sa position, son ordre de plan et ses styles (deuxième surcharge uniquement).

*pParentWnd*<br/>
Pointeur vers la fenêtre parente.

*nID*<br/>
Numéro d’ID de ressource à assigner au contrôle nouvellement créé.

*pControl*<br/>
Instance d’un contrôle Windows Forms à associer à l’objet [CWinFormsControl](../../mfc/reference/cwinformscontrol-class.md) (quatrième surcharge uniquement).

### <a name="return-value"></a>Valeur renvoyée

En cas de réussite, retourne une valeur différente de zéro. En cas d’échec, retourne la valeur zéro.

### <a name="remarks"></a>Notes

Cette méthode instancie une .NET Framework Windows Forms contrôle dans un conteneur MFC.

La première surcharge de la méthode accepte un .NET Framework le type de données *PTYPE* afin que les MFC puissent instancier un nouvel objet de ce type. *PTYPE* doit être un type de données de [type](/dotnet/api/system.type) .

La deuxième surcharge de la méthode crée un contrôle de Windows Forms basé sur le `TManagedControl` paramètre de modèle de la `CWinFormsControl` classe. La taille et la position du contrôle sont basées sur la `RECT` structure passée à la méthode. Seul *dwStyle* est important pour les styles.

La troisième surcharge de la méthode crée un contrôle Windows Forms qui remplace un contrôle statique, en le détruisant et en supposant sa position, son ordre de plan et ses styles. Le contrôle statique sert uniquement d’espace réservé pour le contrôle Windows Forms. Lors de la création du contrôle, cette surcharge combine les styles de *dwStyle* avec les styles de ressources du contrôle statique.

La quatrième surcharge de la méthode vous permet de passer un contrôle de Windows Forms déjà *instancié, que* MFC encapsulera. Elle doit être du même type que le `TManagedControl` paramètre de modèle de la `CWinFormsControl` classe.

Consultez [utilisation d’un contrôle utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md) pour obtenir des exemples sur l’utilisation des contrôles Windows Forms.

## <a name="cwinformscontrolcwinformscontrol"></a><a name="cwinformscontrol"></a> CWinFormsControl::CWinFormsControl

Construit un objet de wrapper de contrôle MFC Windows Forms.

```
CWinFormsControl();
```

### <a name="remarks"></a>Notes

Le contrôle Windows Forms est instancié quand vous appelez [CWinFormsControl :: CreateManagedControl](#createmanagedcontrol).

## <a name="cwinformscontrolgetcontrol"></a><a name="getcontrol"></a> CWinFormsControl::GetControl

Récupère un pointeur désignant le contrôle de Windows Forms.

```
inline TManagedControl^ GetControl() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne un pointeur vers le contrôle Windows Forms.

### <a name="example"></a>Exemple

  Consultez [CWinFormsControl :: CreateManagedControl](#createmanagedcontrol).

## <a name="cwinformscontrolgetcontrolhandle"></a><a name="getcontrolhandle"></a> CWinFormsControl::GetControlHandle

Récupère un handle vers le contrôle de Windows Forms.

```
inline HWND GetControlHandle() const;
```

### <a name="return-value"></a>Valeur renvoyée

Retourne un handle pour le contrôle de Windows Forms.

### <a name="remarks"></a>Notes

`GetControlHandle` est une méthode d’assistance qui retourne le handle de fenêtre stocké dans les propriétés de contrôle .NET Framework. La valeur du handle de fenêtre est copiée dans [CWnd :: m_hWnd](../../mfc/reference/cwnd-class.md#m_hwnd) pendant l’appel à [CWnd :: Attach](../../mfc/reference/cwnd-class.md#attach).

## <a name="cwinformscontroloperator--gt"></a><a name="operator_-_gt"></a> CWinFormsControl :: Operator-&gt;

Remplace [CWinFormsControl :: GetControl](#getcontrol) dans les expressions.

```
inline TManagedControl^  operator->() const;
```

### <a name="remarks"></a>Notes

Cet opérateur fournit une syntaxe pratique qui remplace `GetControl` dans les expressions.

Pour plus d’informations sur la Windows Forms, consultez [utilisation d’un contrôle utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="cwinformscontroloperator-tmanagedcontrol"></a><a name="operator_tmanagedcontrol"></a> CWinFormsControl :: Operator TManagedControl ^

Effectue un cast d’un type en pointeur vers un contrôle de Windows Forms.

```
inline operator TManagedControl^() const;
```

### <a name="remarks"></a>Notes

Cet opérateur passe `CWinFormsControl<TManagedControl>` aux fonctions qui acceptent un pointeur vers un contrôle de Windows Forms.

## <a name="see-also"></a>Voir aussi

[CWinFormsDialog, classe](../../mfc/reference/cwinformsdialog-class.md)<br/>
[CWinFormsView (classe)](../../mfc/reference/cwinformsview-class.md)
