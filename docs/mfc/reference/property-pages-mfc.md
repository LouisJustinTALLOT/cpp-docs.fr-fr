---
description: 'En savoir plus sur : pages de propriétés (MFC)'
title: Pages de propriétés (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- property page data transfer functions in MFC
- property pages [MFC], global MFC functions
ms.assetid: 734f88bc-c776-4136-9b0e-f45c761a45c1
ms.openlocfilehash: fa395272ba74c6b3900d5a1500d4cf47ade4e535
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218964"
---
# <a name="property-pages-mfc"></a>Pages de propriétés (MFC)

Les pages de propriétés affichent les valeurs actuelles des propriétés de contrôle OLE spécifiques dans une interface graphique personnalisable pour l’affichage et la modification en prenant en charge un mécanisme de mappage de données basé sur l’échange de données de boîtes de dialogue (DDX).

Ce mécanisme de mappage de données mappe les contrôles de page de propriétés aux propriétés individuelles du contrôle OLE. La valeur de la propriété du contrôle reflète l’État ou le contenu du contrôle de la page de propriétés. Le mappage entre les contrôles et les propriétés de la page de propriétés est spécifié par **DDP_** appels de fonction dans la fonction membre de la page de propriétés `DoDataExchange` . La liste suivante répertorie les fonctions de **DDP_** qui échangent des données à l’aide de la page de propriétés de votre contrôle :

### <a name="property-page-data-transfer"></a>Transfert de données de page de propriétés

|Nom|Description|
|-|-|
|[DDP_CBIndex](#ddp_cbindex)|Lie l’index de la chaîne sélectionnée dans une zone de liste déroulante avec la propriété d’un contrôle.|
|[DDP_CBString](#ddp_cbstring)|Lie la chaîne sélectionnée dans une zone de liste déroulante à la propriété d’un contrôle. La chaîne sélectionnée peut commencer par les mêmes lettres que la valeur de la propriété, mais elle n’a pas besoin de la faire correspondre entièrement.|
|[DDP_CBStringExact](#ddp_cbstringexact)|Lie la chaîne sélectionnée dans une zone de liste déroulante à la propriété d’un contrôle. La chaîne sélectionnée et la valeur de chaîne de la propriété doivent correspondre exactement.|
|[DDP_Check](#ddp_check)|Lie une case à cocher dans la page de propriétés du contrôle à la propriété d’un contrôle.|
|[DDP_LBIndex](#ddp_lbindex)|Lie l’index de la chaîne sélectionnée dans une zone de liste avec la propriété d’un contrôle.|
|[DDP_LBString](#ddp_lbstring)|Lie la chaîne sélectionnée dans une zone de liste à la propriété d’un contrôle. La chaîne sélectionnée peut commencer par les mêmes lettres que la valeur de la propriété, mais elle n’a pas besoin d’être entièrement identique.|
|[DDP_LBStringExact](#ddp_lbstringexact)|Lie la chaîne sélectionnée dans une zone de liste à la propriété d’un contrôle. La chaîne sélectionnée et la valeur de chaîne de la propriété doivent correspondre exactement.|
|[DDP_PostProcessing](#ddp_postprocessing)|Termine le transfert des valeurs de propriété à partir de votre contrôle.|
|[DDP_Radio](#ddp_radio)|Lie un groupe de cases d’option dans la page de propriétés du contrôle à la propriété d’un contrôle.|
|[DDP_Text](#ddp_text)|Lie un contrôle dans la page de propriétés du contrôle à la propriété d’un contrôle. Cette fonction gère plusieurs types de propriétés différents, tels que **`double`** , **`short`** , BSTR et **`long`** .|

Pour plus d’informations sur la `DoDataExchange` fonction et les pages de propriétés, consultez l’article [contrôles ActiveX : pages de propriétés](../../mfc/mfc-activex-controls-property-pages.md).

La liste suivante répertorie les macros utilisées pour créer et gérer les pages de propriétés d’un contrôle OLE :

### <a name="property-pages"></a>Pages de propriétés

|Nom|Description|
|-|-|
|[BEGIN_PROPPAGEIDS](#begin_proppageids)|Commence la liste des ID de page de propriétés.|
|[END_PROPPAGEIDS](#end_proppageids)|Termine la liste des ID de page de propriétés.|
|[PROPPAGEID](#proppageid)|Déclare une page de propriétés de la classe de contrôle.|

## <a name="ddp_cbindex"></a><a name="ddp_cbindex"></a> DDP_CBIndex

Appelez cette fonction dans la fonction de votre page de propriétés `DoDataExchange` pour synchroniser la valeur d’une propriété entière avec l’index de la sélection actuelle dans une zone de liste déroulante de la page de propriétés.

```cpp
void AFXAPI DDP_CBIndex(
    CDataExchange* pDX,
    int id,
    int& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un `CDataExchange` objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*id*<br/>
ID de ressource du contrôle de zone de liste déroulante associé à la propriété de contrôle spécifiée par *pszPropName*.

*membre*<br/>
Variable membre associée au contrôle de page de propriétés spécifié par *ID* et la propriété spécifiée par *pszPropName*.

*pszPropName*<br/>
Nom de la propriété du contrôle à échanger avec le contrôle de zone de liste déroulante spécifié par *ID*.

### <a name="remarks"></a>Notes

Cette fonction doit être appelée avant l' `DDX_CBIndex` appel de fonction correspondant.

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl. h

## <a name="ddp_cbstring"></a><a name="ddp_cbstring"></a> DDP_CBString

Appelez cette fonction dans la fonction de votre page de propriétés `DoDataExchange` pour synchroniser la valeur d’une propriété de type chaîne avec la sélection actuelle dans une zone de liste déroulante de la page de propriétés.

```cpp
void AFXAPI DDP_CBString(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un `CDataExchange` objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*id*<br/>
ID de ressource du contrôle de zone de liste déroulante associé à la propriété de contrôle spécifiée par *pszPropName*.

*membre*<br/>
Variable membre associée au contrôle de page de propriétés spécifié par *ID* et la propriété spécifiée par *pszPropName*.

*pszPropName*<br/>
Nom de la propriété du contrôle à échanger avec la chaîne de zone de liste déroulante spécifiée par *ID*.

### <a name="remarks"></a>Notes

Cette fonction doit être appelée avant l' `DDX_CBString` appel de fonction correspondant.

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl. h

## <a name="ddp_cbstringexact"></a><a name="ddp_cbstringexact"></a> DDP_CBStringExact

Appelez cette fonction dans la fonction de votre page de propriétés `DoDataExchange` pour synchroniser la valeur d’une propriété de type chaîne qui correspond exactement à la sélection actuelle dans une zone de liste déroulante de la page de propriétés.

```cpp
void AFXAPI DDP_CBStringExact(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un `CDataExchange` objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*id*<br/>
ID de ressource du contrôle de zone de liste déroulante associé à la propriété de contrôle spécifiée par *pszPropName*.

*membre*<br/>
Variable membre associée au contrôle de page de propriétés spécifié par *ID* et la propriété spécifiée par *pszPropName*.

*pszPropName*<br/>
Nom de la propriété du contrôle à échanger avec la chaîne de zone de liste déroulante spécifiée par *ID*.

### <a name="remarks"></a>Notes

Cette fonction doit être appelée avant l' `DDX_CBStringExact` appel de fonction correspondant.

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl. h

## <a name="ddp_check"></a><a name="ddp_check"></a> DDP_Check

Appelez cette fonction dans la fonction de votre page de propriétés `DoDataExchange` pour synchroniser la valeur de la propriété avec le contrôle de case à cocher de la page de propriétés associée.

```cpp
void AFXAPI DDP_Check(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCSTR pszPropName);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un `CDataExchange` objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*id*<br/>
ID de ressource du contrôle de case à cocher associé à la propriété de contrôle spécifiée par *pszPropName*.

*membre*<br/>
Variable membre associée au contrôle de page de propriétés spécifié par *ID* et la propriété spécifiée par *pszPropName*.

*pszPropName*<br/>
Nom de la propriété du contrôle à échanger avec le contrôle de case à cocher spécifié par *ID*.

### <a name="remarks"></a>Notes

Cette fonction doit être appelée avant l' `DDX_Check` appel de fonction correspondant.

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl. h

## <a name="ddp_lbindex"></a><a name="ddp_lbindex"></a> DDP_LBIndex

Appelez cette fonction dans la fonction de votre page de propriétés `DoDataExchange` pour synchroniser la valeur d’une propriété entière avec l’index de la sélection actuelle dans une zone de liste de la page de propriétés.

```cpp
void AFXAPI DDP_LBIndex(
    CDataExchange* pDX,
    int id,
    int& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un `CDataExchange` objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*id*<br/>
ID de ressource du contrôle de zone de liste associé à la propriété de contrôle spécifiée par *pszPropName*.

*membre*<br/>
Variable membre associée au contrôle de page de propriétés spécifié par *ID* et la propriété spécifiée par *pszPropName*.

*pszPropName*<br/>
Nom de la propriété du contrôle à échanger avec la chaîne de zone de liste spécifiée par *ID*.

### <a name="remarks"></a>Notes

Cette fonction doit être appelée avant l' `DDX_LBIndex` appel de fonction correspondant.

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl. h

## <a name="ddp_lbstring"></a><a name="ddp_lbstring"></a> DDP_LBString

Appelez cette fonction dans la fonction de votre page de propriétés `DoDataExchange` pour synchroniser la valeur d’une propriété de type chaîne avec la sélection actuelle dans une zone de liste de la page de propriétés.

```cpp
void AFXAPI DDP_LBString(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un `CDataExchange` objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*id*<br/>
ID de ressource du contrôle de zone de liste associé à la propriété de contrôle spécifiée par *pszPropName*.

*membre*<br/>
Variable membre associée au contrôle de page de propriétés spécifié par *ID* et la propriété spécifiée par *pszPropName*.

*pszPropName*<br/>
Nom de la propriété du contrôle à échanger avec la chaîne de zone de liste spécifiée par *ID*.

### <a name="remarks"></a>Notes

Cette fonction doit être appelée avant l' `DDX_LBString` appel de fonction correspondant.

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl. h

## <a name="ddp_lbstringexact"></a><a name="ddp_lbstringexact"></a> DDP_LBStringExact

Appelez cette fonction dans la fonction de votre page de propriétés `DoDataExchange` pour synchroniser la valeur d’une propriété de type chaîne qui correspond exactement à la sélection actuelle dans une zone de liste de la page de propriétés.

```cpp
void AFXAPI DDP_LBStringExact(
    CDataExchange* pDX,
    int id,
    CString& member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un `CDataExchange` objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*id*<br/>
ID de ressource du contrôle de zone de liste associé à la propriété de contrôle spécifiée par *pszPropName*.

*membre*<br/>
Variable membre associée au contrôle de page de propriétés spécifié par *ID* et la propriété spécifiée par *pszPropName*.

*pszPropName*<br/>
Nom de la propriété du contrôle à échanger avec la chaîne de zone de liste spécifiée par *ID*.

### <a name="remarks"></a>Notes

Cette fonction doit être appelée avant l' `DDX_LBStringExact` appel de fonction correspondant.

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl. h

## <a name="ddp_postprocessing"></a><a name="ddp_postprocessing"></a> DDP_PostProcessing

Appelez cette fonction dans la fonction de votre page de propriétés `DoDataExchange` , pour terminer le transfert des valeurs de propriété de la page de propriétés à votre contrôle lorsque les valeurs de propriété sont enregistrées.

```cpp
void AFXAPI DDP_PostProcessing(CDataExchange * pDX);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un `CDataExchange` objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

### <a name="remarks"></a>Notes

Cette fonction doit être appelée une fois que toutes les fonctions d’échange de données sont terminées. Par exemple :

[!code-cpp[NVC_MFCAxCtl#15](../../mfc/reference/codesnippet/cpp/property-pages-mfc_1.cpp)]

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl. h

## <a name="ddp_radio"></a><a name="ddp_radio"></a> DDP_Radio

Appelez cette fonction dans la fonction de votre contrôle `DoPropExchange` pour synchroniser la valeur de la propriété avec le contrôle de case d’option de la page de propriétés associée.

```cpp
void AFXAPI DDP_Radio(
    CDataExchange* pDX,
    int id,
    int & member,
    LPCTSTR pszPropName);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Pointeur vers un `CDataExchange` objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*id*<br/>
ID de ressource du contrôle de case d’option associé à la propriété de contrôle spécifiée par *pszPropName*.

*membre*<br/>
Variable membre associée au contrôle de page de propriétés spécifié par *ID* et la propriété spécifiée par *pszPropName*.

*pszPropName*<br/>
Nom de la propriété du contrôle à échanger avec le contrôle de case d’option spécifié par *ID*.

### <a name="remarks"></a>Notes

Cette fonction doit être appelée avant l' `DDX_Radio` appel de fonction correspondant.

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl. h

## <a name="ddp_text"></a><a name="ddp_text"></a> DDP_Text

Appelez cette fonction dans la fonction de votre contrôle `DoDataExchange` pour synchroniser la valeur de la propriété avec le contrôle de page de propriétés associé.

```cpp
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

*pDX*<br/>
Pointeur vers un `CDataExchange` objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*id*<br/>
ID de ressource du contrôle associé à la propriété de contrôle spécifiée par *pszPropName*.

*membre*<br/>
Variable membre associée au contrôle de page de propriétés spécifié par *ID* et la propriété spécifiée par *pszPropName*.

*pszPropName*<br/>
Nom de la propriété du contrôle à échanger avec le contrôle spécifié par *ID*.

### <a name="remarks"></a>Notes

Cette fonction doit être appelée avant l' `DDX_Text` appel de fonction correspondant.

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl. h

## <a name="begin_proppageids"></a><a name="begin_proppageids"></a> BEGIN_PROPPAGEIDS

Commence la définition de la liste des ID de page de propriétés de votre contrôle.

```
BEGIN_PROPPAGEIDS(class_name,  count)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Nom de la classe de contrôle pour laquelle les pages de propriétés sont spécifiées.

*count*<br/>
Nombre de pages de propriétés utilisées par la classe de contrôle.

### <a name="remarks"></a>Notes

Dans le fichier d’implémentation (. cpp) qui définit les fonctions membres pour votre classe, démarrez la liste des pages de propriétés avec la macro BEGIN_PROPPAGEIDS, puis ajoutez des entrées de macro pour chacune de vos pages de propriétés, et complétez la liste des pages de propriétés avec la macro END_PROPPAGEIDS.

Pour plus d’informations sur les pages de propriétés, consultez l’article [contrôles ActiveX : pages de propriétés](../../mfc/mfc-activex-controls-property-pages.md).

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl. h

## <a name="end_proppageids"></a><a name="end_proppageids"></a> END_PROPPAGEIDS

Termine la définition de votre liste d’ID de page de propriétés.

```
END_PROPPAGEIDS(class_name)
```

### <a name="parameters"></a>Paramètres

*class_name*<br/>
Nom de la classe de contrôle qui possède la page de propriétés.

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl. h

## <a name="proppageid"></a><a name="proppageid"></a> PROPPAGEID

Ajoute une page de propriétés à utiliser par votre contrôle OLE.

```
PROPPAGEID(clsid)
```

### <a name="parameters"></a>Paramètres

*identificateur*<br/>
ID de classe unique d’une page de propriétés.

### <a name="remarks"></a>Notes

Toutes les macros PROPPAGEID doivent être placées entre les macros BEGIN_PROPPAGEIDS et END_PROPPAGEIDS dans le fichier d’implémentation de votre contrôle.

### <a name="requirements"></a>Spécifications

  **En-tête** afxctl. h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
