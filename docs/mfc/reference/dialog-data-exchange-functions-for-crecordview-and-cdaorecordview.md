---
title: Fonctions d’échange de données de la boîte de dialogue pour CRecordView et CDaoRecordView | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- AFXDAO/DDX_FieldCBIndex
- AFXDAO/DDX_FieldCBString
- AFXDAO/DDX_FieldCBStringExact
- AFXDAO/DDX_FieldCheck
- AFXDAO/DDX_FieldLBIndex
- AFXDAO/DDX_FieldLBString
- AFXDAO/DDX_FieldLBStringExact
- AFXDAO/DDX_FieldRadio
- AFXDAO/DDX_FieldScroll
- AFXDAO/DDX_FieldText
dev_langs:
- C++
helpviewer_keywords:
- DDX_Field functions [MFC]
- ODBC [MFC], dialog data exchange (DDX) support
- DDX (dialog data exchange) [MFC], database support
- DDX (dialog data exchange) [MFC], functions
- databases [MFC], dialog data exchange (DDX) support
- DAO [MFC], dialog data exchange (DDX) support
ms.assetid: 0d8cde38-3a2c-4100-9589-ac80a7b1ce91
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7c2c954851348fcb96b28a4c47aee4b4475aeaca
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50070281"
---
# <a name="dialog-data-exchange-functions-for-crecordview-and-cdaorecordview"></a>Échange de données de boîtes de dialogue pour CRecordView et CDaoRecordView

Cette rubrique répertorie les fonctions DDX_Field utilisées pour échanger des données entre un [CRecordset](../../mfc/reference/crecordset-class.md) et un [CRecordView](../../mfc/reference/crecordview-class.md) formulaire ou un [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) et un [ CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) formulaire.

> [!NOTE]
>  DDX_Field (fonctions) sont comme les fonctions DDX car ils échangent des données avec des contrôles dans un formulaire. Mais contrairement à DDX, ils échangent des données avec les champs de l’objet recordset associé de la vue plutôt qu’avec des champs de la vue de l’enregistrement. Pour plus d’informations, consultez classes `CRecordView` et `CDaoRecordView`.

### <a name="ddxfield-functions"></a>DDX_Field (fonctions)

|||
|-|-|
|[DDX_FieldCBIndex](#ddx_fieldcbindex)|Transfère les données d’entier entre un membre de données de champ de jeu d’enregistrements et de l’index de la sélection actuelle dans une zone de liste déroulante dans un [CRecordView](../../mfc/reference/crecordview-class.md) ou [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md).|
|[DDX_FieldCBString](#ddx_fieldcbstring)|Transferts `CString` zone de données entre un membre de données de champ de jeu d’enregistrements et le contrôle d’édition d’une liste déroulante un `CRecordView` ou `CDaoRecordView`. Lors du déplacement des données à partir de l’ensemble d’enregistrements au contrôle, cette fonction sélectionne l’élément dans la zone de liste déroulante qui commence par les caractères dans la chaîne spécifiée.|
|[DDX_FieldCBStringExact](#ddx_fieldcbstringexact)|Transferts `CString` zone de données entre un membre de données de champ de jeu d’enregistrements et le contrôle d’édition d’une liste déroulante un `CRecordView` ou `CDaoRecordView`. Lors du déplacement des données à partir de l’ensemble d’enregistrements au contrôle, cette fonction sélectionne l’élément dans la zone de liste modifiable correspond exactement à la chaîne spécifiée.|
|[DDX_FieldCheck](#ddx_fieldcheck)|Transfère les données booléennes entre un membre de données de champ de recordset et une case à cocher dans un `CRecordView` ou `CDaoRecordView`.|
|[DDX_FieldLBIndex](#ddx_fieldlbindex)|Transfère les données d’entier entre un membre de données de champ de jeu d’enregistrements et de l’index de la sélection actuelle dans une zone de liste dans un `CRecordView` ou `CDaoRecordView`.|
|[DDX_FieldLBString](#ddx_fieldlbstring)|Gère le transfert de [CString](../../atl-mfc-shared/reference/cstringt-class.md) des données entre un contrôle de zone de liste et les membres de données de champ d’un recordset. Lors du déplacement des données à partir de l’ensemble d’enregistrements au contrôle, cette fonction sélectionne l’élément dans la zone de liste qui commence par les caractères dans la chaîne spécifiée.|
|[DDX_FieldLBStringExact](#ddx_fieldlbstringexact)|Gère le transfert de `CString` des données entre un contrôle de zone de liste et les membres de données de champ d’un recordset. Lors du déplacement des données à partir de l’ensemble d’enregistrements au contrôle, cette fonction sélectionne le premier élément qui correspond exactement à la chaîne spécifiée.|
|[DDX_FieldRadio](#ddx_fieldradio)|Transfère les données d’entier entre un membre de données de champ de jeu d’enregistrements et d’un groupe de cases d’option dans un `CRecordView` ou `CDaoRecordView`.|
|[DDX_FieldScroll](#ddx_fieldscroll)|Définit ou obtient la position de défilement d’un contrôle de barre de défilement dans un `CRecordView` ou `CDaoRecordView`. Appeler à partir de votre [DoFieldExchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange) (fonction).|
|[DDX_FieldSlider](#ddx_fieldslider)|Synchronise la position du curseur de défilement d’un contrôle slider dans une vue d’enregistrement et un `int` membre de données de champ d’un jeu d’enregistrements. |
|[DDX_FieldText](#ddx_fieldtext)|Versions surchargées sont disponibles pour le transfert de `int`, **UINT**, **long**, `DWORD`, [CString](../../atl-mfc-shared/reference/cstringt-class.md), **float** , **double**, **court**, [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md), et [COleCurrency](../../mfc/reference/colecurrency-class.md) des données entre un membre de données de champ de recordset et une modification zone un `CRecordView` ou `CDaoRecordView`.|

##  <a name="ddx_fieldcbindex"></a>  DDX_FieldCBIndex

Le `DDX_FieldCBIndex` fonction synchronise l’index de l’élément sélectionné dans le contrôle de zone de liste d’un contrôle de zone de liste déroulante dans une vue d’enregistrement et un `int` membre de données de champ d’un recordset associé à la vue de l’enregistrement.

```
void AFXAPI DDX_FieldCBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
L’ID d’un contrôle dans le [CRecordView](../../mfc/reference/crecordview-class.md) ou [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objet.

*index*<br/>
Une référence à un membre de données de champ dans associé `CRecordset` ou `CDaoRecordset` objet.

*pRecordset*<br/>
Un pointeur vers le [CRecordset](../../mfc/reference/crecordset-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objet avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lors du déplacement des données à partir de l’ensemble d’enregistrements au contrôle, cette fonction affecte la sélection dans le contrôle en fonction de la valeur spécifiée dans *index*. Sur un transfert à partir de l’ensemble d’enregistrements pour le contrôle, si le champ de jeu d’enregistrements est Null, MFC définit la valeur de l’index 0. Sur un transfert à partir du contrôle vers le recordset, si le contrôle est vide ou si aucun élément n’est sélectionné, le champ de jeu d’enregistrements est défini sur 0.

Utilisez la première version si vous travaillez avec les classes basées sur ODBC. Utilisez la deuxième version si vous travaillez avec les classes DAO.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md). Pour plus d’informations sur le mécanisme DDX des et des exemples [CRecordView](../../mfc/reference/crecordview-class.md) et [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) champs, consultez l’article [vues d’enregistrements](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Exemple

Consultez [DDX_FieldText](#ddx_fieldtext) pour obtenir un exemple DDX_Field général. L’exemple serait similaire pour `DDX_FieldCBIndex`.

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdao.h

##  <a name="ddx_fieldcbstring"></a>  DDX_FieldCBString

Le `DDX_FieldCBString` fonction gère le transfert de [CString](../../atl-mfc-shared/reference/cstringt-class.md) des données entre le contrôle d’édition d’un contrôle de zone de liste déroulante dans une vue d’enregistrement et un `CString` membre de données de champ d’un recordset associé à la vue de l’enregistrement.

```
void AFXAPI DDX_FieldCBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
L’ID d’un contrôle dans le [CRecordView](../../mfc/reference/crecordview-class.md) ou [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objet.

*valeur*<br/>
Une référence à un membre de données de champ dans associé `CRecordset` ou `CDaoRecordset` objet.

*pRecordset*<br/>
Un pointeur vers le [CRecordset](../../mfc/reference/crecordset-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objet avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lors du déplacement des données à partir de l’ensemble d’enregistrements au contrôle, cette fonction affecte la sélection actuelle dans la zone de liste déroulante pour la première ligne qui commence par les caractères dans la chaîne spécifiée dans *valeur*. Sur un transfert à partir de l’ensemble d’enregistrements pour le contrôle, si le champ de jeu d’enregistrements est Null, n’importe quelle sélection est supprimée de la zone de liste déroulante et le contrôle d’édition de la zone de liste déroulante est défini sur une valeur vide. Sur un transfert à partir du contrôle vers le recordset, si le contrôle est vide, le champ de jeu d’enregistrements est défini avec la valeur Null si le champ autorise.

Utilisez la première version si vous travaillez avec les classes basées sur ODBC. Utilisez la deuxième version si vous travaillez avec les classes DAO.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md). Pour plus d’informations sur le mécanisme DDX des et des exemples [CRecordView](../../mfc/reference/crecordview-class.md) et [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) champs, consultez l’article [vues d’enregistrements](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Exemple

Consultez [DDX_FieldText](#ddx_fieldtext) pour obtenir un exemple DDX_Field général. L’exemple inclut un appel à `DDX_FieldCBString`.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdao.h

## <a name="ddx_fieldcbstringexact"></a>  DDX_FieldCBStringExact

Le `DDX_FieldCBStringExact` fonction gère le transfert de [CString](../../atl-mfc-shared/reference/cstringt-class.md) des données entre le contrôle d’édition d’un contrôle de zone de liste déroulante dans une vue d’enregistrement et un `CString` membre de données de champ d’un recordset associé à la vue de l’enregistrement.

```
void AFXAPI DDX_FieldCBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
L’ID d’un contrôle dans le [CRecordView](../../mfc/reference/crecordview-class.md) ou [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objet.

*valeur*<br/>
Une référence à un membre de données de champ dans associé `CRecordset` ou `CDaoRecordset` objet.

*pRecordset*<br/>
Un pointeur vers le [CRecordset](../../mfc/reference/crecordset-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objet avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lors du déplacement des données à partir de l’ensemble d’enregistrements au contrôle, cette fonction affecte la sélection actuelle dans la zone de liste déroulante pour la première ligne qui correspond exactement à la chaîne spécifiée dans *valeur*. Sur un transfert à partir de l’ensemble d’enregistrements pour le contrôle, si le champ de jeu d’enregistrements est NULL, n’importe quelle sélection est supprimée de la zone de liste déroulante et la zone d’édition de la zone de liste déroulante est définie sur une valeur vide. Sur un transfert à partir du contrôle vers le recordset, si le contrôle est vide, le champ de jeu d’enregistrements est défini sur NULL.

Utilisez la première version si vous travaillez avec les classes basées sur ODBC. Utilisez la deuxième version si vous travaillez avec les classes DAO.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md). Pour plus d’informations sur le mécanisme DDX des et des exemples [CRecordView](../../mfc/reference/crecordview-class.md) et [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) champs, consultez l’article [vues d’enregistrements](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Exemple

Consultez [DDX_FieldText](#ddx_fieldtext) pour obtenir un exemple DDX_Field général. Les appels à `DDX_FieldCBStringExact` serait similaire.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdao.h

##  <a name="ddx_fieldcheck"></a>  DDX_FieldCheck

Le `DDX_FieldCheck` fonction gère le transfert de **int** des données entre un contrôle check box dans une boîte de dialogue, vue de formulaire ou objet de vue de contrôle et un **int** membre de données de la boîte de dialogue, le mode formulaire ou le contrôle objet de vue.

```
void AFXAPI DDX_FieldCheck(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldCheck(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
L’ID de ressource du contrôle de case à cocher associé à la propriété du contrôle.

*valeur*<br/>
Une référence à une variable membre de la boîte de dialogue, vue de formulaire ou objet de vue de contrôle avec lequel les données sont échangées.

*pRecordset*<br/>
Un pointeur vers le [CRecordset](../../mfc/reference/crecordset-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objet avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lorsque `DDX_FieldCheck` est appelée, *valeur* est défini sur l’état actuel du contrôle de case à cocher, ou l’état du contrôle est définie sur *valeur*, selon la direction du transfert.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md).

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdao.h

##  <a name="ddx_fieldlbindex"></a>  DDX_FieldLBIndex

Le `DDX_FieldLBIndex` fonction synchronise l’index de l’élément sélectionné dans un contrôle de zone de liste dans une vue d’enregistrement et un **int** membre de données de champ d’un recordset associé à la vue de l’enregistrement.

```
void AFXAPI DDX_FieldLBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBIndex(
    CDataExchange* pDX,
    int nIDC,
    int& index,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
L’ID d’un contrôle dans le [CRecordView](../../mfc/reference/crecordview-class.md) ou [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objet.

*index*<br/>
Une référence à un membre de données de champ dans associé `CRecordset` ou `CDaoRecordset` objet.

*pRecordset*<br/>
Un pointeur vers le [CRecordset](../../mfc/reference/crecordset-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objet avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lors du déplacement des données à partir de l’ensemble d’enregistrements au contrôle, cette fonction affecte la sélection dans le contrôle en fonction de la valeur spécifiée dans *index*. Sur un transfert à partir de l’ensemble d’enregistrements pour le contrôle, si le champ de jeu d’enregistrements est Null, MFC définit la valeur de l’index 0. Sur un transfert à partir du contrôle vers le recordset, si le contrôle est vide, le champ de jeu d’enregistrements est défini sur 0.

Utilisez la première version si vous travaillez avec les classes basées sur ODBC. Utilisez la deuxième version si vous travaillez avec les classes DAO.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md). Pour plus d’informations sur le mécanisme DDX des et des exemples [CRecordView](../../mfc/reference/crecordview-class.md) et [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) champs, consultez l’article [vues d’enregistrements](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Exemple

Consultez [DDX_FieldText](#ddx_fieldtext) pour obtenir un exemple DDX_Field général.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdao.h

##  <a name="ddx_fieldlbstring"></a>  DDX_FieldLBString

Le `DDX_FieldLBString` copie la sélection actuelle d’un contrôle de zone de liste dans une vue d’enregistrement pour un [CString](../../atl-mfc-shared/reference/cstringt-class.md) membre de données de champ d’un recordset associé à la vue de l’enregistrement.

```
void AFXAPI DDX_FieldLBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBString(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
L’ID d’un contrôle dans le [CRecordView](../../mfc/reference/crecordview-class.md) ou [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objet.

*valeur*<br/>
Une référence à un membre de données de champ dans associé `CRecordset` ou `CDaoRecordset` objet.

*pRecordset*<br/>
Un pointeur vers le [CRecordset](../../mfc/reference/crecordset-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objet avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Dans le sens inverse, cette fonction affecte la sélection actuelle dans la zone de liste pour la première ligne qui commence par les caractères dans la chaîne spécifiée par *valeur*. Sur un transfert à partir de l’ensemble d’enregistrements pour le contrôle, si le champ de jeu d’enregistrements est Null, n’importe quelle sélection est supprimée à partir de la zone de liste. Sur un transfert à partir du contrôle vers le recordset, si le contrôle est vide, le champ de jeu d’enregistrements est défini sur Null.

Utilisez la première version si vous travaillez avec les classes basées sur ODBC. Utilisez la deuxième version si vous travaillez avec les classes DAO.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md). Pour plus d’informations sur le mécanisme DDX des et des exemples [CRecordView](../../mfc/reference/crecordview-class.md) et [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) champs, consultez l’article [vues d’enregistrements](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Exemple

Consultez [DDX_FieldText](#ddx_fieldtext) pour obtenir un exemple DDX_Field général. Les appels à `DDX_FieldLBString` serait similaire.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdao.h

##  <a name="ddx_fieldlbstringexact"></a>  DDX_FieldLBStringExact

Le `DDX_FieldLBStringExact` fonction copie la sélection actuelle d’un contrôle de zone de liste dans une vue d’enregistrement pour un [CString](../../atl-mfc-shared/reference/cstringt-class.md) membre de données de champ d’un recordset associé à la vue de l’enregistrement.

```
void AFXAPI DDX_FieldLBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldLBStringExact(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
L’ID d’un contrôle dans le [CRecordView](../../mfc/reference/crecordview-class.md) ou [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objet.

*valeur*<br/>
Une référence à un membre de données de champ dans associé `CRecordset` ou `CDaoRecordset` objet.

*pRecordset*<br/>
Un pointeur vers le [CRecordset](../../mfc/reference/crecordset-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objet avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Dans le sens inverse, cette fonction affecte la sélection actuelle dans la zone de liste pour la première ligne qui correspond exactement à la chaîne spécifiée dans *valeur*. Sur un transfert à partir de l’ensemble d’enregistrements pour le contrôle, si le champ de jeu d’enregistrements est Null, n’importe quelle sélection est supprimée à partir de la zone de liste. Sur un transfert à partir du contrôle vers le recordset, si le contrôle est vide, le champ de jeu d’enregistrements est défini sur Null.

Utilisez la première version si vous travaillez avec les classes basées sur ODBC. Utilisez la deuxième version si vous travaillez avec les classes DAO.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md). Pour plus d’informations sur le mécanisme DDX des et des exemples [CRecordView](../../mfc/reference/crecordview-class.md) et [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) champs, consultez l’article [vues d’enregistrements](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Exemple

Consultez [DDX_FieldText](#ddx_fieldtext) pour obtenir un exemple DDX_Field général. Les appels à `DDX_FieldLBStringExact` serait similaire.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdao.h

##  <a name="ddx_fieldradio"></a>  DDX_FieldRadio

Le `DDX_FieldRadio` fonction associe de base zéro **int** variable de membre du jeu d’enregistrements d’une vue de l’enregistrement avec le bouton de case d’option actuellement sélectionnée dans un groupe de cases d’option dans la vue de l’enregistrement.

```
void AFXAPI DDX_FieldRadio(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldRadio(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
L’ID de la première dans un groupe (avec le style WS_GROUP) des contrôles de bouton radio adjacent dans la [CRecordView](../../mfc/reference/crecordview-class.md) ou [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objet.

*valeur*<br/>
Une référence à un membre de données de champ dans associé `CRecordset` ou `CDaoRecordset` objet.

*pRecordset*<br/>
Un pointeur vers le [CRecordset](../../mfc/reference/crecordset-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objet avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lors du transfert à partir du champ de jeu d’enregistrements à la vue, cette fonction est active le *nième* case (de base zéro) et désactive les autres boutons. Dans le sens inverse, cette fonction définit le champ de jeu d’enregistrements sur le nombre ordinal de la case d’option qui est actuellement activée (cochée). Sur un transfert à partir de l’ensemble d’enregistrements pour le contrôle, si le champ de jeu d’enregistrements est Null, aucun bouton n’est sélectionné. Sur un transfert à partir du contrôle vers le recordset, si aucun contrôle n’est sélectionné, le champ de jeu d’enregistrements est défini avec la valeur Null si le champ qui le permet.

Utilisez la première version si vous travaillez avec les classes basées sur ODBC. Utilisez la deuxième version si vous travaillez avec les classes DAO.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md). Pour plus d’informations sur le mécanisme DDX des et des exemples [CRecordView](../../mfc/reference/crecordview-class.md) et [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) champs, consultez l’article [vues d’enregistrements](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Exemple

Consultez [DDX_FieldText](#ddx_fieldtext) pour obtenir un exemple DDX_Field général. Les appels à `DDX_FieldRadio` serait similaire.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdao.h

##  <a name="ddx_fieldscroll"></a>  DDX_FieldScroll

Le `DDX_FieldScroll` fonction synchronise la position de défilement d’un contrôle de barre de défilement dans une vue d’enregistrement et un **int** membre de données de champ d’un jeu d’enregistrements associés à la vue d’enregistrement (ou toute variable de type entier vous souhaitez mapper à) .

```
void AFXAPI DDX_FieldScroll(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldScroll(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
L’ID de la première dans un groupe (avec le style WS_GROUP) des contrôles de bouton radio adjacent dans la [CRecordView](../../mfc/reference/crecordview-class.md) ou [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objet.

*valeur*<br/>
Une référence à un membre de données de champ dans associé `CRecordset` ou `CDaoRecordset` objet.

*pRecordset*<br/>
Un pointeur vers le [CRecordset](../../mfc/reference/crecordset-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objet avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lors du déplacement des données à partir de l’ensemble d’enregistrements au contrôle, cette fonction affecte la valeur spécifiée dans la position de défilement du contrôle de barre de défilement *valeur*. Sur un transfert à partir de l’ensemble d’enregistrements pour le contrôle, si le champ de jeu d’enregistrements est Null, le contrôle de barre de défilement est défini sur 0. Sur un transfert à partir du contrôle vers le recordset, si le contrôle est vide, la valeur du champ de jeu d’enregistrements est 0.

Utilisez la première version si vous travaillez avec les classes basées sur ODBC. Utilisez la deuxième version si vous travaillez avec les classes DAO.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md). Pour plus d’informations sur le mécanisme DDX des et des exemples [CRecordView](../../mfc/reference/crecordview-class.md) et [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) champs, consultez l’article [vues d’enregistrements](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Exemple

Consultez [DDX_FieldText](#ddx_fieldtext) pour obtenir un exemple DDX_Field général. Les appels à `DDX_FieldScroll` serait similaire.

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdao.h

  ## <a name="nameddxfieldslidera--ddxfieldslider"></a>name="ddx_fieldslider"></a>  DDX_FieldSlider
Le `DDX_FieldSlider` fonction synchronise la position du curseur de défilement d’un contrôle slider dans une vue d’enregistrement et un **int** membre de données de champ d’un jeu d’enregistrements associés à la vue d’enregistrement (ou toute variable de type entier vous souhaitez mapper à).

### <a name="syntax"></a>Syntaxe

  ```
   void AFXAPI DDX_FieldSlider(
       CDataExchange* pDX,
       int nIDC,
       int& value,
       CRecordset* pRecordset );

void AFXAPI DDX_FieldSlider(
   CDataExchange* pDX,
   int nIDC,
   int& value,
   CDaoRecordset* pRecordset );
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Un pointeur vers un [CDataExchange](cdataexchange-class.md) objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
L’ID de ressource du contrôle slider.

*valeur*<br/>
Une référence à la valeur à échanger. Ce paramètre conserve ou sera utilisée pour définir la position de curseur de défilement actuelle du contrôle slider.

*pRecordset*<br/>
Un pointeur vers associé `CRecordset` ou `CDaoRecordset` objet avec lequel les données sont échangées.

### <a name="remarks"></a>Notes

Lors du déplacement des données à partir de l’ensemble d’enregistrements au curseur, cette fonction définit la position du curseur à la valeur spécifiée dans *valeur*. Sur un transfert à partir de l’ensemble d’enregistrements pour le contrôle, si le champ de jeu d’enregistrements est Null, position du contrôle de curseur est définie sur 0. Sur un transfert à partir du contrôle vers le recordset, si le contrôle est vide, la valeur du champ de jeu d’enregistrements est 0.

`DDX_FieldSlider` ne pas échanger les informations de plage avec des contrôles slider capables de définir une plage plutôt que simplement d’une position.

Utilisez le premier remplacement de la fonction si vous travaillez avec les classes basées sur ODBC. Utilisez le deuxième remplacement avec les classes DAO.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../dialog-data-exchange-and-validation.md). Pour plus d’informations sur le mécanisme DDX des et des exemples `CRecordView` et `CDaoRecordView` champs, consultez [vues d’enregistrements](../../data/record-views-mfc-data-access.md). Pour plus d’informations sur les contrôles de curseur, consultez [à l’aide de CSliderCtrl](../using-csliderctrl.md).

### <a name="example"></a>Exemple

Consultez [DDX_FieldText](#ddx_fieldtext) pour obtenir un exemple DDX_Field général. Les appels à `DDX_FieldSlider` serait similaire.

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdao.h

### <a name="see-also"></a>Voir aussi

[Macros et objet Globals](mfc-macros-and-globals.md)

##  <a name="ddx_fieldtext"></a>  DDX_FieldText

Le `DDX_FieldText` fonction gère le transfert de **int**, **court**, **long**, DWORD, [CString](../../atl-mfc-shared/reference/cstringt-class.md), **float**, **double**, **BOOL**, ou **octets** des données entre un contrôle de zone d’édition et les membres de données de champ d’un recordset.

```
void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    BYTE& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    int& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    UINT& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    long& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    float& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    double& value,
    CRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    short& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    BOOL& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    BYTE& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    long& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    DWORD& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    CString& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    float& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    double& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    COleDateTime& value,
    CDaoRecordset* pRecordset);

void AFXAPI DDX_FieldText(
    CDataExchange* pDX,
    int nIDC,
    COleCurrency& value,
    CDaoRecordset* pRecordset);
```

### <a name="parameters"></a>Paramètres

*pDX*<br/>
Un pointeur vers un [CDataExchange](../../mfc/reference/cdataexchange-class.md) objet. L’infrastructure fournit cet objet pour établir le contexte de l’échange de données, notamment sa direction.

*nIDC*<br/>
L’ID d’un contrôle dans le [CRecordView](../../mfc/reference/crecordview-class.md) ou [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) objet.

*valeur*<br/>
Une référence à un membre de données de champ dans associé `CRecordset` ou `CDaoRecordset` objet. Le type de données de valeur varie en fonction des versions surchargées de `DDX_FieldText` vous utilisez.

*pRecordset*<br/>
Un pointeur vers le [CRecordset](../../mfc/reference/crecordset-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objet avec lequel les données sont échangées. Permet à ce pointeur `DDX_FieldText` pour détecter et définir des valeurs Null.

### <a name="remarks"></a>Notes

Pour [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objets, `DDX_FieldText` gère également le transfert [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md), et [COleCurrency](../../mfc/reference/colecurrency-class.md) valeurs. Un contrôle de zone d’édition vide indique une valeur Null. Sur un transfert à partir de l’ensemble d’enregistrements pour le contrôle, si le champ de jeu d’enregistrements est Null, la zone d’édition est définie sur une valeur vide. Sur un transfert à partir du contrôle vers le recordset, si le contrôle est vide, le champ de jeu d’enregistrements est défini sur Null.

Utilisez les versions avec [CRecordset](../../mfc/reference/crecordset-class.md) paramètres si vous travaillez avec les classes basées sur ODBC. Utilisez les versions avec [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) paramètres si vous travaillez avec les classes DAO.

Pour plus d'informations sur DDX, consultez [Échange et validation de données de boîtes de dialogue](../../mfc/dialog-data-exchange-and-validation.md). Pour plus d’informations sur le mécanisme DDX des et des exemples [CRecordView](../../mfc/reference/crecordview-class.md) et [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) champs, consultez l’article [vues d’enregistrements](../../data/record-views-mfc-data-access.md).

### <a name="example"></a>Exemple

Ce qui suit `DoDataExchange` fonctionner pour un [CRecordView](../../mfc/reference/crecordview-class.md) contient `DDX_FieldText` fonction appelle pour trois types de données : `IDC_COURSELIST` est une zone de liste déroulante ; les deux autres contrôles sont des zones d’édition. Pour la programmation de DAO, le *m_pSet* paramètre est un pointeur vers un [CRecordset](../../mfc/reference/crecordset-class.md) ou [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

[!code-cpp[NVC_MFCDatabase#43](../../mfc/codesnippet/cpp/dialog-data-exchange-functions-for-crecordview-and-cdaorecordview_1.cpp)]

### <a name="requirements"></a>Configuration requise

  **En-tête** afxdao.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
