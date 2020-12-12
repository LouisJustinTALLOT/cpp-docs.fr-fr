---
description: 'En savoir plus sur : CWinFormsView, classe'
title: CWinFormsView (classe)
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
ms.openlocfilehash: 09dad434ebe0e0011fef5836196fd15e25390536
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318427"
---
# <a name="cwinformsview-class"></a>CWinFormsView (classe)

Fournit les fonctionnalités génériques pour l'hébergement d'un contrôle Windows Forms en tant que vue MFC.

## <a name="syntax"></a>Syntaxe

```
class CWinFormsView : public CView;
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CWinFormsView :: CWinFormsView](#cwinformsview)|Construit un objet `CWinFormsView`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CWinFormsView :: GetControl](#getcontrol)|Récupère un pointeur désignant le contrôle de Windows Forms.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-|
|[CWinFormsView :: Operator, contrôle ^](#operator_control)|Effectue un cast d’un type en pointeur vers un contrôle de Windows Forms.|

## <a name="remarks"></a>Notes

MFC utilise la `CWinFormsView` classe pour héberger un contrôle .NET Framework Windows Forms dans une vue MFC. Le contrôle est un enfant de la vue native et occupe toute la zone cliente de la vue MFC. Le résultat est similaire à une `CFormView` vue, ce qui vous permet de tirer parti du concepteur de Windows Forms et du moment de l’exécution pour créer des vues riches basées sur des formulaires.

Pour plus d’informations sur l’utilisation de Windows Forms, consultez [utilisation d’un contrôle utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

> [!NOTE]
> L’intégration des Windows Forms MFC fonctionne uniquement dans les projets qui sont liés de manière dynamique aux MFC (projets dans lesquels AFXDLL est défini).

> [!NOTE]
> CWinFormsView ne prend pas en charge la fenêtre fractionné MFC ( [classe CSplitterWnd](../../mfc/reference/csplitterwnd-class.md)). Actuellement, seul le contrôle Splitter Windows Forms est pris en charge.

## <a name="requirements"></a>Spécifications

**En-tête :** afxwinforms. h

## <a name="cwinformsviewcwinformsview"></a><a name="cwinformsview"></a> CWinFormsView :: CWinFormsView

Construit un objet `CWinFormsView`.

```
CWinFormsView(System::Type^ pManagedViewType);
```

### <a name="parameters"></a>Paramètres

*pManagedViewType*<br/>
Pointeur vers le type de données du contrôle utilisateur Windows Forms.

### <a name="example"></a>Exemple

Dans l’exemple suivant, la `CUserView` classe hérite de `CWinFormsView` et passe le type de `UserControl1` au `CWinFormsView` constructeur. `UserControl1` est un contrôle personnalisé dans ControlLibrary1.dll.

[!code-cpp[NVC_MFC_Managed#1](../../mfc/reference/codesnippet/cpp/cwinformsview-class_1.h)]

[!code-cpp[NVC_MFC_Managed#2](../../mfc/reference/codesnippet/cpp/cwinformsview-class_2.cpp)]

## <a name="cwinformsviewgetcontrol"></a><a name="getcontrol"></a> CWinFormsView :: GetControl

Récupère un pointeur désignant le contrôle de Windows Forms.

```
System::Windows::Forms::Control^ GetControl() const;
```

### <a name="return-value"></a>Valeur renvoyée

Pointeur vers un objet `System.Windows.Forms.Control`.

### <a name="remarks"></a>Notes

Pour obtenir un exemple d’utilisation de Windows Forms, consultez [utilisation d’un contrôle utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="cwinformsviewoperator-control"></a><a name="operator_control"></a> CWinFormsView :: Operator, contrôle ^

Effectue un cast d’un type en pointeur vers un contrôle de Windows Forms.

```
operator System::Windows::Forms::Control^() const;
```

### <a name="remarks"></a>Notes

Cet opérateur vous permet de passer une `CWinFormsView` vue aux fonctions qui acceptent un pointeur vers un contrôle de Windows Forms de type <xref:System.Windows.Forms.Control> .

### <a name="example"></a>Exemple

  Consultez [CWinFormsView :: GetControl](#getcontrol).

## <a name="see-also"></a>Voir aussi

[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CWinFormsControl, classe](../../mfc/reference/cwinformscontrol-class.md)<br/>
[CWinFormsDialog, classe](../../mfc/reference/cwinformsdialog-class.md)<br/>
[CFormView, classe](../../mfc/reference/cformview-class.md)
