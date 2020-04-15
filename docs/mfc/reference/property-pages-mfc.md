---
title: Pages de propriétés (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- property page data transfer functions in MFC
- property pages [MFC], global MFC functions
ms.assetid: 734f88bc-c776-4136-9b0e-f45c761a45c1
ms.openlocfilehash: 1064cd99d1820ae8865fa632c3097441172c78c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372999"
---
# <a name="property-pages-mfc"></a>Pages de propriétés (MFC)

Les pages de propriété affichent les valeurs actuelles de propriétés de contrôle OLE spécifiques dans une interface graphique personnalisable pour la visualisation et l’édition en soutenant un mécanisme de cartographie des données basé sur l’échange de données de dialogue (DDX).

Ce mécanisme de cartographie des données cartographie les commandes de la page de propriété aux propriétés individuelles du contrôle OLE. La valeur de la propriété de contrôle reflète l’état ou le contenu du contrôle de la page de propriété. La cartographie entre les commandes de **DDP_** la page de propriété et les `DoDataExchange` propriétés est spécifiée par DDP_ les appels de fonction dans la fonction membre de la page de propriété. Voici une liste de **fonctions DDP_** qui échangent les données saisies à l’aide de la page de propriété de votre contrôle :

### <a name="property-page-data-transfer"></a>Transfert de données de la page de propriété

|||
|-|-|
|[DDP_CBIndex](#ddp_cbindex)|Relie l’index de la chaîne sélectionnée dans une boîte combo avec la propriété d’un contrôle.|
|[DDP_CBString](#ddp_cbstring)|Relie la chaîne sélectionnée dans une boîte combo avec la propriété d’un contrôle. La chaîne sélectionnée peut commencer par les mêmes lettres que la valeur de la propriété, mais n’a pas besoin de l’assortir entièrement.|
|[DDP_CBStringExact](#ddp_cbstringexact)|Relie la chaîne sélectionnée dans une boîte combo avec la propriété d’un contrôle. La chaîne sélectionnée et la valeur de chaîne de la propriété doivent correspondre exactement.|
|[DDP_Check](#ddp_check)|Relie une case à cocher dans la page de propriété du contrôleur avec la propriété d’un contrôle.|
|[DDP_LBIndex](#ddp_lbindex)|Relie l’index de la chaîne sélectionnée dans une boîte de liste avec la propriété d’un contrôle.|
|[DDP_LBString](#ddp_lbstring)|Relie la chaîne sélectionnée dans une boîte de liste avec la propriété d’un contrôle. La chaîne sélectionnée peut commencer avec les mêmes lettres que la valeur de la propriété, mais n’a pas besoin de l’égaler entièrement.|
|[DDP_LBStringExact](#ddp_lbstringexact)|Relie la chaîne sélectionnée dans une boîte de liste avec la propriété d’un contrôle. La chaîne sélectionnée et la valeur de chaîne de la propriété doivent correspondre exactement.|
|[DDP_PostProcessing](#ddp_postprocessing)|Termine le transfert des valeurs des propriétés de votre contrôle.|
|[DDP_Radio](#ddp_radio)|Relie un groupe de boutons radio dans la page de propriété du contrôle avec la propriété d’un contrôle.|
|[DDP_Text](#ddp_text)|Relie un contrôle dans la page de propriété du contrôle avec la propriété d’un contrôle. Cette fonction gère plusieurs types différents de propriétés, telles que **double**, **court**, BSTR, et **long**.|

Pour plus d’informations sur les `DoDataExchange` pages fonction et propriété, voir l’article [ActiveX Controls: Property Pages](../../mfc/mfc-activex-controls-property-pages.md).

Voici une liste de macros utilisées pour créer et gérer les pages de propriété pour un contrôle OLE :

### <a name="property-pages"></a>Pages de propriétés

|||
|-|-|
|[BEGIN_PROPPAGEIDS](#begin_proppageids)|Commence la liste des numéros d’ID de la page de propriété.|
|[END_PROPPAGEIDS](#end_proppageids)|Termine la liste des numéros d’adresse.|
|[PROPPAGEID](#proppageid)|Déclare une page de propriété de la classe de contrôle.|

## <a name="ddp_cbindex"></a><a name="ddp_cbindex"></a>DDP_CBIndex

Appelez cette fonction dans la `DoDataExchange` fonction de votre page de propriété pour synchroniser la valeur d’une propriété d’intégrage avec l’index de la sélection actuelle dans une boîte de combo sur la page de propriété.

```
void AFXAPI DDP_CBIndex(
    CDataExchange* pDX,
    int id,
    int& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Pointeur `CDataExchange` vers un objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*id*<br/>
L’ID de ressource du contrôle de la boîte combo associé à la propriété de contrôle spécifiée par *pszPropName*.

*Membre*<br/>
La variable du membre associée au contrôle de la page de propriété spécifiée par *id* et à la propriété spécifiée par *pszPropName*.

*pszPropName (en)*<br/>
Le nom de propriété de la propriété de contrôle à échanger avec le contrôle de la boîte combo spécifié par *id*.

### <a name="remarks"></a>Notes

Cette fonction doit être `DDX_CBIndex` appelée avant l’appel de fonction correspondant.

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl.h

## <a name="ddp_cbstring"></a><a name="ddp_cbstring"></a>DDP_CBString

Appelez cette fonction dans la `DoDataExchange` fonction de votre page de propriété pour synchroniser la valeur d’une propriété de chaîne avec la sélection actuelle dans une boîte de combo sur la page de propriété.

```
void AFXAPI DDP_CBString(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Pointeur `CDataExchange` vers un objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*id*<br/>
L’ID de ressource du contrôle de la boîte combo associé à la propriété de contrôle spécifiée par *pszPropName*.

*Membre*<br/>
La variable du membre associée au contrôle de la page de propriété spécifiée par *id* et à la propriété spécifiée par *pszPropName*.

*pszPropName (en)*<br/>
Le nom de propriété de la propriété de contrôle à échanger avec la chaîne de boîte combo spécifié par *id*.

### <a name="remarks"></a>Notes

Cette fonction doit être `DDX_CBString` appelée avant l’appel de fonction correspondant.

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl.h

## <a name="ddp_cbstringexact"></a><a name="ddp_cbstringexact"></a>DDP_CBStringExact

Appelez cette fonction dans la `DoDataExchange` fonction de votre page de propriété pour synchroniser la valeur d’une propriété à cordes qui correspond exactement à la sélection actuelle dans une boîte combo sur la page de propriété.

```
void AFXAPI DDP_CBStringExact(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Pointeur `CDataExchange` vers un objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*id*<br/>
L’ID de ressource du contrôle de la boîte combo associé à la propriété de contrôle spécifiée par *pszPropName*.

*Membre*<br/>
La variable du membre associée au contrôle de la page de propriété spécifiée par *id* et à la propriété spécifiée par *pszPropName*.

*pszPropName (en)*<br/>
Le nom de propriété de la propriété de contrôle à échanger avec la chaîne de boîte combo spécifié par *id*.

### <a name="remarks"></a>Notes

Cette fonction doit être `DDX_CBStringExact` appelée avant l’appel de fonction correspondant.

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl.h

## <a name="ddp_check"></a><a name="ddp_check"></a>DDP_Check

Appelez cette fonction dans la `DoDataExchange` fonction de votre page de propriété pour synchroniser la valeur de la propriété avec le contrôle de la boîte de cocher de page de propriété associée.

```
void AFXAPI DDP_Check(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCSTR pszPropName);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Pointeur `CDataExchange` vers un objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*id*<br/>
L’ID de ressource du contrôle de la case à cocher associé à la propriété de contrôle spécifiée par *pszPropName*.

*Membre*<br/>
La variable du membre associée au contrôle de la page de propriété spécifiée par *id* et à la propriété spécifiée par *pszPropName*.

*pszPropName (en)*<br/>
Le nom de propriété de la propriété de contrôle à échanger avec le contrôle de la case à cocher spécifié par *id*.

### <a name="remarks"></a>Notes

Cette fonction doit être `DDX_Check` appelée avant l’appel de fonction correspondant.

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl.h

## <a name="ddp_lbindex"></a><a name="ddp_lbindex"></a>DDP_LBIndex

Appelez cette fonction dans la `DoDataExchange` fonction de votre page de propriété pour synchroniser la valeur d’une propriété d’intégrage avec l’index de la sélection actuelle dans une boîte de liste sur la page de propriété.

```
void AFXAPI DDP_LBIndex(
    CDataExchange* pDX,
    int id,
    int& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Pointeur `CDataExchange` vers un objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*id*<br/>
L’ID de ressource du contrôle de la boîte de liste associé à la propriété de contrôle spécifiée par *pszPropName*.

*Membre*<br/>
La variable du membre associée au contrôle de la page de propriété spécifiée par *id* et à la propriété spécifiée par *pszPropName*.

*pszPropName (en)*<br/>
Le nom de propriété de la propriété de contrôle à échanger avec la chaîne de boîte de liste spécifiée par *id*.

### <a name="remarks"></a>Notes

Cette fonction doit être `DDX_LBIndex` appelée avant l’appel de fonction correspondant.

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl.h

## <a name="ddp_lbstring"></a><a name="ddp_lbstring"></a>DDP_LBString

Appelez cette fonction dans la `DoDataExchange` fonction de votre page de propriété pour synchroniser la valeur d’une propriété de chaîne avec la sélection actuelle dans une boîte de liste sur la page de propriété.

```
void AFXAPI DDP_LBString(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Pointeur `CDataExchange` vers un objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*id*<br/>
L’ID de ressource du contrôle de la boîte de liste associé à la propriété de contrôle spécifiée par *pszPropName*.

*Membre*<br/>
La variable du membre associée au contrôle de la page de propriété spécifiée par *id* et à la propriété spécifiée par *pszPropName*.

*pszPropName (en)*<br/>
Le nom de propriété de la propriété de contrôle à échanger avec la chaîne de boîte de liste spécifiée par *id*.

### <a name="remarks"></a>Notes

Cette fonction doit être `DDX_LBString` appelée avant l’appel de fonction correspondant.

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl.h

## <a name="ddp_lbstringexact"></a><a name="ddp_lbstringexact"></a>DDP_LBStringExact

Appelez cette fonction dans la `DoDataExchange` fonction de votre page de propriété pour synchroniser la valeur d’une propriété à cordes qui correspond exactement à la sélection actuelle dans une boîte de liste sur la page de propriété.

```
void AFXAPI DDP_LBStringExact(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Pointeur `CDataExchange` vers un objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*id*<br/>
L’ID de ressource du contrôle de la boîte de liste associé à la propriété de contrôle spécifiée par *pszPropName*.

*Membre*<br/>
La variable du membre associée au contrôle de la page de propriété spécifiée par *id* et à la propriété spécifiée par *pszPropName*.

*pszPropName (en)*<br/>
Le nom de propriété de la propriété de contrôle à échanger avec la chaîne de boîte de liste spécifiée par *id*.

### <a name="remarks"></a>Notes

Cette fonction doit être `DDX_LBStringExact` appelée avant l’appel de fonction correspondant.

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl.h

## <a name="ddp_postprocessing"></a><a name="ddp_postprocessing"></a>DDP_PostProcessing

Appelez cette fonction dans la `DoDataExchange` fonction de votre page de propriété, pour terminer le transfert des valeurs de propriété de la page de propriété à votre contrôle lorsque les valeurs de propriété sont enregistrées.

```
void AFXAPI DDP_PostProcessing(CDataExchange * pDX);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Pointeur `CDataExchange` vers un objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

### <a name="remarks"></a>Notes

Cette fonction doit être appelée une fois toutes les fonctions d’échange de données terminées. Par exemple :

[!code-cpp[NVC_MFCAxCtl#15](../../mfc/reference/codesnippet/cpp/property-pages-mfc_1.cpp)]

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl.h

## <a name="ddp_radio"></a><a name="ddp_radio"></a>DDP_Radio

Appelez cette fonction dans `DoPropExchange` la fonction de votre contrôle pour synchroniser la valeur de la propriété avec le contrôle de bouton radio de la page de propriété associée.

```
void AFXAPI DDP_Radio(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Pointeur `CDataExchange` vers un objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*id*<br/>
L’ID de ressource du contrôle de bouton radio associé à la propriété de commande spécifiée par *pszPropName*.

*Membre*<br/>
La variable du membre associée au contrôle de la page de propriété spécifiée par *id* et à la propriété spécifiée par *pszPropName*.

*pszPropName (en)*<br/>
Le nom de propriété de la propriété de contrôle à échanger avec le contrôle du bouton radio spécifié par *id*.

### <a name="remarks"></a>Notes

Cette fonction doit être `DDX_Radio` appelée avant l’appel de fonction correspondant.

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl.h

## <a name="ddp_text"></a><a name="ddp_text"></a>DDP_Text

Appelez cette fonction dans `DoDataExchange` la fonction de votre contrôle pour synchroniser la valeur de la propriété avec le contrôle de la page de propriété associée.

```
void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    BYTE & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    UINT & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    long & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    DWORD & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    float & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    double & member,
    LPCTSTR pszPropName);

void AFXAPI DDP_Text(
    CDataExchange* pDX,
    int id,
    CString & member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Paramètres

*Pdx*<br/>
Pointeur `CDataExchange` vers un objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*id*<br/>
L’ID de ressource du contrôle associé à la propriété de contrôle spécifiée par *pszPropName*.

*Membre*<br/>
La variable du membre associée au contrôle de la page de propriété spécifiée par *id* et à la propriété spécifiée par *pszPropName*.

*pszPropName (en)*<br/>
Le nom de propriété de la propriété de contrôle à échanger avec le contrôle spécifié par *id*.

### <a name="remarks"></a>Notes

Cette fonction doit être `DDX_Text` appelée avant l’appel de fonction correspondant.

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl.h

## <a name="begin_proppageids"></a><a name="begin_proppageids"></a>BEGIN_PROPPAGEIDS

Commence la définition de la liste de votre contrôle des numéros de page de propriété.

```
BEGIN_PROPPAGEIDS(class_name,  count)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Le nom de la classe de contrôle pour laquelle les pages de propriété sont spécifiées.

*count*<br/>
Nombre de pages de propriété utilisées par la classe de contrôle.

### <a name="remarks"></a>Notes

Dans le fichier d’implémentation (.cpp) qui définit les fonctions des membres pour votre classe, démarrez la liste de page de propriété avec la BEGIN_PROPPAGEIDS macro, puis ajoutez des entrées macro pour chacune de vos pages de propriété, et remplissez la liste de page de propriété avec la macro END_PROPPAGEIDS.

Pour plus d’informations sur les pages de propriété, voir l’article [ActiveX Controls: Property Pages](../../mfc/mfc-activex-controls-property-pages.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl.h

## <a name="end_proppageids"></a><a name="end_proppageids"></a>END_PROPPAGEIDS

Termine la définition de votre liste d’identification de page de propriété.

```
END_PROPPAGEIDS(class_name)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Le nom de la classe de contrôle qui possède la page de propriété.

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl.h

## <a name="proppageid"></a><a name="proppageid"></a>PROPPAGEID

Ajoute une page de propriété pour une utilisation par votre contrôle OLE.

```
PROPPAGEID(clsid)
```

### <a name="parameters"></a>Paramètres

*clsid*<br/>
L’ID de classe unique d’une page de propriété.

### <a name="remarks"></a>Notes

Toutes les macros PROPPAGEID doivent être placées entre les macros BEGIN_PROPPAGEIDS et END_PROPPAGEIDS dans le fichier de mise en œuvre de votre contrôle.

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
