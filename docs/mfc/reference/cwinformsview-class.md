---
title: CWinFormsView, classe
ms.date: 11/04/2016
f1_keywords:
- CWinFormsView
- AFXWINFORMS/CWinFormsView
- AFXWINFORMS/CWinFormsView::CWinFormsView
- AFXWINFORMS/CWinFormsView::GetControl
helpviewer_keywords:
- CWinFormsView [MFC], CWinFormsView
- CWinFormsView [MFC], GetControl
ms.assetid: d597e397-6529-469b-88f5-7f65a6b9e895
ms.openlocfilehash: 766ce3e0db192cc416b17531864a75d721bfc4ae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50597510"
---
# <a name="cwinformsview-class"></a>CWinFormsView, classe

Fournit les fonctionnalités génériques pour l'hébergement d'un contrôle Windows Forms en tant que vue MFC.

## <a name="syntax"></a>Syntaxe

```
class CWinFormsView : public CView;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CWinFormsView::CWinFormsView](#cwinformsview)|Construit un objet `CWinFormsView`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CWinFormsView::GetControl](#getcontrol)|Récupère un pointeur vers le contrôle Windows Forms.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Name||
|----------|-|
|[Contrôle de CWinFormsView::operator ^](#operator_control)|Effectue un cast d’un type en un pointeur vers un contrôle Windows Forms.|

## <a name="remarks"></a>Notes

MFC utilise le `CWinFormsView` classe pour héberger un contrôle Windows Forms de .NET Framework au sein d’une vue MFC. Le contrôle est un enfant de la vue native et occupe la zone cliente de la vue MFC. Le résultat est similaire à un `CFormView` vue, ce qui vous permet de tirer parti du Concepteur Windows Forms et l’exécution pour créer des vues basées sur le formulaire riches.

Pour plus d’informations sur l’utilisation de Windows Forms, consultez [à l’aide d’un contrôle d’utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

> [!NOTE]
>  Intégration de MFC Windows Forms fonctionne uniquement dans les projets qui se lient dynamiquement avec MFC (projets dans lesquels AFXDLL est défini).

> [!NOTE]
>  CWinFormsView ne prend pas en charge la fenêtre de séparateur MFC ( [CSplitterWnd, classe](../../mfc/reference/csplitterwnd-class.md)). Actuellement uniquement Windows Forms séparateur contrôle est pris en charge.

## <a name="requirements"></a>Configuration requise

**En-tête :** afxwinforms.h

##  <a name="cwinformsview"></a>  CWinFormsView::CWinFormsView

Construit un objet `CWinFormsView`.

```
CWinFormsView(System::Type^ pManagedViewType);
```

### <a name="parameters"></a>Paramètres

*pManagedViewType*<br/>
Pointeur vers le type de données du contrôle utilisateur Windows Forms.

### <a name="example"></a>Exemple

Dans l’exemple suivant, le `CUserView` hérite de la classe `CWinFormsView` et transmet le type de `UserControl1` à la `CWinFormsView` constructeur. `UserControl1` est un contrôle personnalisé dans ControlLibrary1.dll.

[!code-cpp[NVC_MFC_Managed#1](../../mfc/reference/codesnippet/cpp/cwinformsview-class_1.h)]

[!code-cpp[NVC_MFC_Managed#2](../../mfc/reference/codesnippet/cpp/cwinformsview-class_2.cpp)]

##  <a name="getcontrol"></a>  CWinFormsView::GetControl

Récupère un pointeur vers le contrôle Windows Forms.

```
System::Windows::Forms::Control^ GetControl() const;
```

### <a name="return-value"></a>Valeur de retour

Pointeur vers un objet `System.Windows.Forms.Control` .

### <a name="remarks"></a>Notes

Pour obtenir un exemple montrant comment utiliser Windows Forms, consultez [à l’aide d’un contrôle d’utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

##  <a name="operator_control"></a>  Contrôle de CWinFormsView::operator ^

Effectue un cast d’un type en un pointeur vers un contrôle Windows Forms.

```
operator System::Windows::Forms::Control^() const;
```

### <a name="remarks"></a>Notes

Cet opérateur vous permet de transmettre un `CWinFormsView` vue aux fonctions qui acceptent un pointeur vers un contrôle Windows Forms de type <xref:System.Windows.Forms.Control>.

### <a name="example"></a>Exemple

  Consultez [CWinFormsView::GetControl](#getcontrol).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWinFormsControl, classe](../../mfc/reference/cwinformscontrol-class.md)<br/>
[CWinFormsDialog, classe](../../mfc/reference/cwinformsdialog-class.md)<br/>
[CFormView, classe](../../mfc/reference/cformview-class.md)
