---
title: Classe de CWinFormsControl | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CWinFormsControl
- AFXWINFORMS/CWinFormsControl
- AFXWINFORMS/CWinFormsControl::CWinFormsControl
- AFXWINFORMS/CWinFormsControl::CreateManagedControl
- AFXWINFORMS/CWinFormsControl::GetControl
- AFXWINFORMS/CWinFormsControl::GetControlHandle
dev_langs:
- C++
helpviewer_keywords:
- CWinFormsControl [MFC], CWinFormsControl
- CWinFormsControl [MFC], CreateManagedControl
- CWinFormsControl [MFC], GetControl
- CWinFormsControl [MFC], GetControlHandle
ms.assetid: 6406dd7b-fb89-4a18-ac3a-c010d6b6289a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 00ec945c5f0cdbb0c12f49b90719c31bf841ef2f
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37121635"
---
# <a name="cwinformscontrol-class"></a>Classe de CWinFormsControl
Fournit les fonctionnalités de base pour l'hébergement d'un contrôle Windows Forms.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<class TManagedControl>  
class CWinFormsControl : public CWnd  
```  
  
#### <a name="parameters"></a>Paramètres  
 `TManagedControl`  
 Un contrôle Windows Forms de .NET Framework à afficher dans l’application MFC.  
  
## <a name="members"></a>Membres  
  
### <a name="public-constructors"></a>Constructeurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CWinFormsControl::CWinFormsControl](#cwinformscontrol)|Construit un objet de wrapper de contrôle Windows Forms de MFC.|  
  
### <a name="public-methods"></a>M&#233;thodes publiques  
  
|Nom|Description|  
|----------|-----------------|  
|[CWinFormsControl::CreateManagedControl](#createmanagedcontrol)|Crée un contrôle Windows Forms dans un conteneur de MFC.|  
|[CWinFormsControl::GetControl](#getcontrol)|Récupère un pointeur vers le contrôle Windows Forms.|  
|[CWinFormsControl::GetControlHandle](#getcontrolhandle)|Récupère un handle vers le contrôle Windows Forms.|  
  
### <a name="public-operators"></a>Op&#233;rateurs publics  
  
|Nom|Description|  
|----------|-----------------|  
|[CWinFormsControl::operator-&gt;](#operator_-_gt)|Remplace [CWinFormsControl::GetControl](#getcontrol) dans les expressions.|  
|[CWinFormsControl::operator TManagedControl ^](#operator_tmanagedcontrol)|Convertit un type comme un pointeur vers un contrôle Windows Forms.|  
  
## <a name="remarks"></a>Notes  
 La `CWinFormsControl` classe fournit les fonctionnalités de base pour l’hébergement d’un contrôle Windows Forms.  
  
 Pour plus d’informations sur l’utilisation de Windows Forms, consultez [à l’aide d’un contrôle d’utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
 Votre code MFC pas doit mettre en cache les handles de fenêtre (généralement stockées dans `m_hWnd`). Certaines propriétés du contrôle Windows Forms exigent que Win32 sous-jacent `Window` détruit et recréé à l’aide de `DestroyWindow` et `CreateWindow`. Les handles d’implémentation MFC Windows Forms le `Destroy` et `Create` événements des contrôles pour mettre à jour le `m_hWnd` membre.  
  
> [!NOTE]
>  Intégration de MFC Windows Forms fonctionne uniquement dans les projets qui se lient dynamiquement avec MFC (dans lesquels AFXDLL est défini).  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afxwinforms.h  
  
##  <a name="createmanagedcontrol"></a>  CWinFormsControl::CreateManagedControl  
 Crée un contrôle Windows Forms dans un conteneur de MFC.  
  
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
 *PTapez*  
 Le type de données du contrôle à créer. Doit être un [Type](https://msdn.microsoft.com/en-us/library/system.type) type de données.  
  
 *dwStyle*  
 Le style de fenêtre à appliquer au contrôle. Spécifier une combinaison de [Styles de fenêtre](../../mfc/reference/styles-used-by-mfc.md#window-styles). Actuellement, seuls les styles suivants sont pris en charge : WS_TABSTOP, WS_VISIBLE, WS_DISABLED et WS_GROUP.  
  
 *Rect*  
 A [Rect, Structure](../../mfc/reference/rect-structure1.md) qui définit les coordonnées des angles supérieur gauche et à droite du contrôle (tout d’abord surcharge uniquement).  
  
 *nPlaceHolderID*  
 Le handle du contrôle statique titulaire placé dans l’éditeur de ressources. Le contrôle Windows Forms nouvellement créé remplace le contrôle statique, en supposant que sa position, ordre de plan et des styles (seconde surcharge uniquement).  
  
 *pParentWnd*  
 Pointeur vers la fenêtre parente.  
  
 *nID*  
 Le numéro d’ID de ressource à affecter au contrôle nouvellement créé.  
  
 *pControl*  
 Une instance d’un contrôle Windows Forms à associer à la [CWinFormsControl](../../mfc/reference/cwinformscontrol-class.md) (surcharge quatrième uniquement) de l’objet.  
  
### <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne une valeur différente de zéro. En cas d’échec, retourne la valeur zéro.  
  
### <a name="remarks"></a>Notes  
 Cette méthode instancie un contrôle Windows Forms .NET Framework dans un conteneur de MFC.  
  
 La première surcharge de la méthode accepte un type de données .NET Framework *PTapez* pour que MFC pouvez instancier un nouvel objet de ce type. *PTapez* doit être un [Type](https://msdn.microsoft.com/en-us/library/system.type) type de données.  
  
 La deuxième surcharge de la méthode crée un contrôle Windows Forms en fonction de la `TManagedControl` paramètre de modèle de la `CWinFormsControl` classe. La taille et la position du contrôle est basé sur le `RECT` structure passée à la méthode. Uniquement *dwStyle* est importante pour les styles.  
  
 La troisième surcharge de la méthode crée un contrôle Windows Forms qui remplace un contrôle statique, détruire et en supposant que sa position, ordre de plan et des styles. Le contrôle statique sert uniquement un espace réservé pour le contrôle Windows Forms. Lorsque vous créez le contrôle, cette surcharge combine les styles de *dwStyle* avec des styles de ressource d' un contrôle statique.  
  
 La quatrième surcharge de la méthode vous permet de passer d’un contrôle Windows Forms déjà instancié *pControl* qui encapsule MFC. Elle doit être du même type que le `TManagedControl` paramètre de modèle de la `CWinFormsControl` classe.  
  
 Consultez [à l’aide d’un contrôle d’utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md) pour obtenir des exemples sur l’utilisation de Windows Form contrôle.  
  
##  <a name="cwinformscontrol"></a>  CWinFormsControl::CWinFormsControl  
 Construit un objet de wrapper de contrôle Windows Forms de MFC.  
  
```  
CWinFormsControl();
```  
  
### <a name="remarks"></a>Notes  
 Le contrôle Windows Forms est instancié lorsque vous appelez [CWinFormsControl::CreateManagedControl](#createmanagedcontrol).  
  
##  <a name="getcontrol"></a>  CWinFormsControl::GetControl  
 Récupère un pointeur vers le contrôle Windows Forms.  
  
```  
inline TManagedControl^ GetControl() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un pointeur vers le contrôle Windows Forms.  
  
### <a name="example"></a>Exemple  
  Consultez [CWinFormsControl::CreateManagedControl](#createmanagedcontrol).  
  
##  <a name="getcontrolhandle"></a>  CWinFormsControl::GetControlHandle  
 Récupère un handle vers le contrôle Windows Forms.  
  
```  
inline HWND GetControlHandle() const;  
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne un handle vers le contrôle Windows Forms.  
  
### <a name="remarks"></a>Notes  
 `GetControlHandle` est une méthode d’assistance qui retourne le handle de fenêtre stocké dans les propriétés de contrôle de .NET Framework. La valeur de handle de fenêtre est copiée vers [CWnd::m_hWnd](../../mfc/reference/cwnd-class.md#m_hwnd) lors de l’appel à [CWnd::Attach](../../mfc/reference/cwnd-class.md#attach).  
  
##  <a name="operator_-_gt"></a>  CWinFormsControl::operator-&gt;  
 Remplace [CWinFormsControl::GetControl](#getcontrol) dans les expressions.  
  
```  
inline TManagedControl^  operator->() const;  
```  
  
### <a name="remarks"></a>Notes  
 Cet opérateur fournit une syntaxe qui remplace `GetControl` dans les expressions.  
  
 Pour plus d’informations sur les Windows Forms, consultez [à l’aide d’un contrôle d’utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).  
  
##  <a name="operator_tmanagedcontrol"></a>  CWinFormsControl::operator TManagedControl ^  
 Convertit un type comme un pointeur vers un contrôle Windows Forms.  
  
```  
inline operator TManagedControl^() const;  
```  
  
### <a name="remarks"></a>Notes  
 Cet opérateur passe `CWinFormsControl<TManagedControl>` à des fonctions qui acceptent un pointeur vers un contrôle Windows Forms.  
  
## <a name="see-also"></a>Voir aussi  
 [Classe de CWinFormsDialog](../../mfc/reference/cwinformsdialog-class.md)   
 [CWinFormsView, classe](../../mfc/reference/cwinformsview-class.md)
