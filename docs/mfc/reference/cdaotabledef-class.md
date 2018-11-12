---
title: CDaoTableDef, classe
ms.date: 11/04/2016
f1_keywords:
- CDaoTableDef
- AFXDAO/CDaoTableDef
- AFXDAO/CDaoTableDef::CDaoTableDef
- AFXDAO/CDaoTableDef::Append
- AFXDAO/CDaoTableDef::CanUpdate
- AFXDAO/CDaoTableDef::Close
- AFXDAO/CDaoTableDef::Create
- AFXDAO/CDaoTableDef::CreateField
- AFXDAO/CDaoTableDef::CreateIndex
- AFXDAO/CDaoTableDef::DeleteField
- AFXDAO/CDaoTableDef::DeleteIndex
- AFXDAO/CDaoTableDef::GetAttributes
- AFXDAO/CDaoTableDef::GetConnect
- AFXDAO/CDaoTableDef::GetDateCreated
- AFXDAO/CDaoTableDef::GetDateLastUpdated
- AFXDAO/CDaoTableDef::GetFieldCount
- AFXDAO/CDaoTableDef::GetFieldInfo
- AFXDAO/CDaoTableDef::GetIndexCount
- AFXDAO/CDaoTableDef::GetIndexInfo
- AFXDAO/CDaoTableDef::GetName
- AFXDAO/CDaoTableDef::GetRecordCount
- AFXDAO/CDaoTableDef::GetSourceTableName
- AFXDAO/CDaoTableDef::GetValidationRule
- AFXDAO/CDaoTableDef::GetValidationText
- AFXDAO/CDaoTableDef::IsOpen
- AFXDAO/CDaoTableDef::Open
- AFXDAO/CDaoTableDef::RefreshLink
- AFXDAO/CDaoTableDef::SetAttributes
- AFXDAO/CDaoTableDef::SetConnect
- AFXDAO/CDaoTableDef::SetName
- AFXDAO/CDaoTableDef::SetSourceTableName
- AFXDAO/CDaoTableDef::SetValidationRule
- AFXDAO/CDaoTableDef::SetValidationText
- AFXDAO/CDaoTableDef::m_pDAOTableDef
- AFXDAO/CDaoTableDef::m_pDatabase
helpviewer_keywords:
- CDaoTableDef [MFC], CDaoTableDef
- CDaoTableDef [MFC], Append
- CDaoTableDef [MFC], CanUpdate
- CDaoTableDef [MFC], Close
- CDaoTableDef [MFC], Create
- CDaoTableDef [MFC], CreateField
- CDaoTableDef [MFC], CreateIndex
- CDaoTableDef [MFC], DeleteField
- CDaoTableDef [MFC], DeleteIndex
- CDaoTableDef [MFC], GetAttributes
- CDaoTableDef [MFC], GetConnect
- CDaoTableDef [MFC], GetDateCreated
- CDaoTableDef [MFC], GetDateLastUpdated
- CDaoTableDef [MFC], GetFieldCount
- CDaoTableDef [MFC], GetFieldInfo
- CDaoTableDef [MFC], GetIndexCount
- CDaoTableDef [MFC], GetIndexInfo
- CDaoTableDef [MFC], GetName
- CDaoTableDef [MFC], GetRecordCount
- CDaoTableDef [MFC], GetSourceTableName
- CDaoTableDef [MFC], GetValidationRule
- CDaoTableDef [MFC], GetValidationText
- CDaoTableDef [MFC], IsOpen
- CDaoTableDef [MFC], Open
- CDaoTableDef [MFC], RefreshLink
- CDaoTableDef [MFC], SetAttributes
- CDaoTableDef [MFC], SetConnect
- CDaoTableDef [MFC], SetName
- CDaoTableDef [MFC], SetSourceTableName
- CDaoTableDef [MFC], SetValidationRule
- CDaoTableDef [MFC], SetValidationText
- CDaoTableDef [MFC], m_pDAOTableDef
- CDaoTableDef [MFC], m_pDatabase
ms.assetid: 7c5d2254-8475-43c4-8a6c-2d32ead194c9
ms.openlocfilehash: b2f431b250da4b791c06a629315d59bbc7935802
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579234"
---
# <a name="cdaotabledef-class"></a>CDaoTableDef, classe

Représente la définition stockée d'une table de base ou d'une table attachée.

## <a name="syntax"></a>Syntaxe

```
class CDaoTableDef : public CObject
```

## <a name="members"></a>Membres

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CDaoTableDef::CDaoTableDef](#cdaotabledef)|Construit un objet `CDaoTableDef`.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CDaoTableDef::Append](#append)|Ajoute une nouvelle table à la base de données.|
|[CDaoTableDef::CanUpdate](#canupdate)|Retourne zéro si la table peut être mis à jour (vous pouvez modifier la définition des champs ou propriétés de la table).|
|[CDaoTableDef::Close](#close)|Ferme un tabledef ouvert.|
|[CDaoTableDef::Create](#create)|Crée une table qui peut être ajoutée à la base de données à l’aide [Append](#append).|
|[CDaoTableDef::CreateField](#createfield)|Appelé pour créer un champ pour une table.|
|[CDaoTableDef::CreateIndex](#createindex)|Appelée pour créer un index pour une table.|
|[CDaoTableDef::DeleteField](#deletefield)|Appelé pour supprimer un champ d’une table.|
|[CDaoTableDef::DeleteIndex](#deleteindex)|Appelé pour supprimer un index d’une table.|
|[CDaoTableDef::GetAttributes](#getattributes)|Retourne une valeur qui indique une ou plusieurs caractéristiques d’un `CDaoTableDef` objet.|
|[CDaoTableDef::GetConnect](#getconnect)|Retourne une valeur qui fournit des informations sur la source d’une table.|
|[CDaoTableDef::GetDateCreated](#getdatecreated)|Retourne la date et l’heure de la table de base sous-jacente un `CDaoTableDef` objet a été créé.|
|[CDaoTableDef::GetDateLastUpdated](#getdatelastupdated)|Retourne la date et l’heure de la dernière modification apportée à la conception de la table de base.|
|[CDaoTableDef::GetFieldCount](#getfieldcount)|Retourne une valeur qui représente le nombre de champs dans la table.|
|[CDaoTableDef::GetFieldInfo](#getfieldinfo)|Retourne des informations sur les champs particuliers dans la table.|
|[CDaoTableDef::GetIndexCount](#getindexcount)|Retourne le nombre d’index pour la table.|
|[CDaoTableDef::GetIndexInfo](#getindexinfo)|Retourne des types spécifiques d’informations sur les index pour la table.|
|[CDaoTableDef::GetName](#getname)|Retourne le nom défini par l’utilisateur de la table.|
|[CDaoTableDef::GetRecordCount](#getrecordcount)|Retourne le nombre d’enregistrements dans la table.|
|[CDaoTableDef::GetSourceTableName](#getsourcetablename)|Retourne une valeur qui spécifie le nom de la table jointe dans la base de données source.|
|[CDaoTableDef::GetValidationRule](#getvalidationrule)|Retourne une valeur qui valide les données dans un champ comme il est modifié ou ajouté à une table.|
|[CDaoTableDef::GetValidationText](#getvalidationtext)|Retourne une valeur qui spécifie le texte du message que votre application affiche si la valeur d’un objet de champ ne satisfait pas la règle de validation spécifié.|
|[CDaoTableDef::IsOpen](#isopen)|Retourne zéro si la table est ouvre.|
|[CDaoTableDef::Open](#open)|Ouvre un objet tabledef existant stocké dans la base de données 's collection de TableDef.|
|[CDaoTableDef::RefreshLink](#refreshlink)|Met à jour les informations de connexion pour une table attachée.|
|[CDaoTableDef::SetAttributes](#setattributes)|Définit une valeur qui indique une ou plusieurs caractéristiques d’un `CDaoTableDef` objet.|
|[CDaoTableDef::SetConnect](#setconnect)|Définit une valeur qui fournit des informations sur la source d’une table.|
|[CDaoTableDef::SetName](#setname)|Définit le nom de la table.|
|[CDaoTableDef::SetSourceTableName](#setsourcetablename)|Définit une valeur qui spécifie le nom d’une table attachée dans la base de données source.|
|[CDaoTableDef::SetValidationRule](#setvalidationrule)|Définit une valeur qui valide les données dans un champ comme il est modifié ou ajouté à une table.|
|[CDaoTableDef::SetValidationText](#setvalidationtext)|Définit une valeur qui spécifie le texte du message que votre application affiche si la valeur d’un objet de champ ne satisfait pas la règle de validation spécifié.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CDaoTableDef::m_pDAOTableDef](#m_pdaotabledef)|Pointeur vers l’interface DAO sous-jacent à l’objet tabledef.|
|[CDaoTableDef::m_pDatabase](#m_pdatabase)|Base de données source pour cette table.|

## <a name="remarks"></a>Notes

Chaque objet de base de données DAO gère une collection, appelée TableDefs, qui contient tous les objets de tabledef DAO enregistrés.

Vous manipulez une définition de table en utilisant un `CDaoTableDef` objet. Par exemple, vous pouvez :

- Examiner la structure de champ et les index d’une table locale, jointe ou externe dans une base de données.

- Appeler le `SetConnect` et `SetSourceTableName` fonctions membres pour les tables jointes et l’utilisation du `RefreshLink` fonction membre à mettre à jour des connexions à des tables attachées.

- Appelez le `CanUpdate` fonction membre pour déterminer si vous pouvez modifier les définitions de champ dans la table.

- Obtenir ou définir des conditions de validation à l’aide de la `GetValidationRule` et `SetValidationRule`et le `GetValidationText` et `SetValidationText` fonctions membres.

- Utilisez le `Open` fonction membre pour créer un type d’instantané, feuille de réponse dynamique ou table `CDaoRecordset` objet.

    > [!NOTE]
    >  Les classes de base de données DAO sont distinctes des classes de base de données MFC basées sur ODBC Open Database Connectivity (). Tous les noms de classe de base de données DAO ont le préfixe « CDao ». Vous pouvez toujours accès aux sources de données ODBC avec les classes DAO ; les classes DAO offrent généralement des fonctionnalités supérieures, car elles sont spécifiques au moteur de base de données Microsoft Jet.

### <a name="to-use-tabledef-objects-either-to-work-with-an-existing-table-or-to-create-a-new-table"></a>Pour utiliser les objets tabledef pour travailler avec une table existante ou créer une nouvelle table

1. Dans tous les cas, tout d’abord construire un `CDaoTableDef` objet, en fournissant un pointeur vers un [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) de l’objet auquel appartient la table.

1. Ensuite, procédez comme suit, selon ce que vous souhaitez :

   - Pour utiliser un enregistrement de table existant, appelez l’objet tabledef [Open](#open) fonction membre, en fournissant le nom de la table enregistrée.

   - Pour créer une nouvelle table, appelez l’objet tabledef [créer](#create) fonction membre, en fournissant le nom de la table. Appelez [CreateField](#createfield) et [CreateIndex](#createindex) pour ajouter des champs et des index à la table.

   - Appelez [Append](#append) pour enregistrer la table en l’ajoutant au TableDefs (collection) de la base de données. `Create` place cet objet dans un état ouvert, c’est le cas après avoir appelé `Create` vous n’appelez pas `Open`.

        > [!TIP]
        >  Pour créer des tables enregistrées, la plus simple consiste à les créer et de les stocker dans votre base de données à l’aide de Microsoft Access. Vous pouvez ensuite ouvrir et les utiliser dans votre code MFC.

Pour utiliser l’objet tabledef avoir ouvert ou créé, créer et ouvrir un `CDaoRecordset` objet, en spécifiant le nom de cet objet avec un `dbOpenTable` valeur dans le *nOpenType* paramètre.

Utilisation d’un objet tabledef pour créer un `CDaoRecordset` de l’objet, vous en général, créez ou ouvrez un objet tabledef comme indiqué ci-dessus, puis construisez un objet recordset, en passant un pointeur à votre objet tabledef lorsque vous appelez [CDaoRecordset::Open](../../mfc/reference/cdaorecordset-class.md#open). Cet objet que vous passez doit être dans un état ouvert. Pour plus d’informations, consultez la classe [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

Lorsque vous avez terminé à l’aide d’un objet tabledef, appelez sa [fermer](../../mfc/reference/cdaorecordset-class.md#close) membre de fonction ; puis détruisez l’objet tabledef.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CDaoTableDef`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxdao.h

##  <a name="append"></a>  CDaoTableDef::Append

Appelez cette fonction membre après avoir appelé [créer](#create) pour créer un nouvel objet tabledef pour enregistrer cet objet dans la base de données.

```
virtual void Append();
```

### <a name="remarks"></a>Notes

La fonction ajoute l’objet à TableDefs (collection) de la base de données. Vous pouvez utiliser cet objet comme un objet temporaire lors de la définition il en l’ajoutant ne pas, mais si vous souhaitez enregistrer et l’utiliser, vous devez appeler `Append`.

> [!NOTE]
>  Si vous essayez d’ajouter une tabledef sans nom (contenant une chaîne null ou vide), MFC lève une exception.

Pour plus d’informations, consultez la rubrique « Ajout de la méthode » dans l’aide de DAO.

##  <a name="canupdate"></a>  CDaoTableDef::CanUpdate

Appelez cette fonction membre pour déterminer si la définition de la table sous-jacente une `CDaoTableDef` objet peut être modifié.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si la structure de table (schéma) peut être modifiée (ajouter ou supprimer des champs et les index), sinon, 0.

### <a name="remarks"></a>Notes

Par défaut, une nouvelle table sous-jacente une `CDaoTableDef` objet peut être mis à jour et une table jointe sous-jacent un `CDaoTableDef` objet ne peut pas être mis à jour. Un `CDaoTableDef` objet peut être mis à jour, même si le jeu d’enregistrements qui en résulte n’est pas modifiable.

Pour plus d’informations, consultez la rubrique « Propriété actualisable » dans l’aide de DAO.

##  <a name="cdaotabledef"></a>  CDaoTableDef::CDaoTableDef

Construit un objet `CDaoTableDef`.

```
CDaoTableDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>Paramètres

*pDatabase*<br/>
Un pointeur vers un [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objet.

### <a name="remarks"></a>Notes

Après la construction de l’objet, vous devez appeler la [créer](#create) ou [Open](#open) fonction membre. Lorsque vous avez terminé avec l’objet, vous devez appeler sa [fermer](#close) membre de fonction et de détruire le `CDaoTableDef` objet.

##  <a name="close"></a>  CDaoTableDef::Close

Appelez cette fonction membre pour fermer et libérer l’objet tabledef.

```
virtual void Close();
```

### <a name="remarks"></a>Notes

Généralement après l’appel `Close`, vous supprimez l’objet tabledef si elle a été allouée avec **nouveau**.

Vous pouvez appeler [Open](#open) à nouveau après l’appel `Close`. Cela vous permet de réutiliser l’objet tabledef.

Pour plus d’informations, consultez la rubrique « Méthode Close » dans l’aide de DAO.

##  <a name="create"></a>  CDaoTableDef::Create

Appelez cette fonction membre pour créer une table enregistrée.

```
virtual void Create(
    LPCTSTR lpszName,
    long lAttributes = 0,
    LPCTSTR lpszSrcTable = NULL,
    LPCTSTR lpszConnect = NULL);
```

### <a name="parameters"></a>Paramètres

*Caractère*<br/>
Un pointeur vers une chaîne contenant le nom de la table.

*lAttributes*<br/>
Une valeur correspondant aux caractéristiques de la table représentée par l’objet tabledef. Vous pouvez utiliser l’opération de bits OR pour combiner une des constantes suivantes :

|Constante|Description|
|--------------|-----------------|
|`dbAttachExclusive`|Pour les bases de données qui utilisent le moteur de base de données Microsoft Jet, indique la table est une table attachée ouverte pour une utilisation exclusive.|
|`dbAttachSavePWD`|Pour les bases de données qui utilisent le moteur de base de données Microsoft Jet, indique que l’ID utilisateur et le mot de passe pour la table jointe sont enregistrées avec les informations de connexion.|
|`dbSystemObject`|Indique la table est une table système fournie par le moteur de base de données Microsoft Jet.|
|`dbHiddenObject`|Indique la table est une table masquée fournie par le moteur de base de données Microsoft Jet.|

*lpszSrcTable*<br/>
Un pointeur vers une chaîne contenant le nom de la table source. Par défaut, cette valeur est initialisée avec la valeur NULL.

*lpszConnect*<br/>
Un pointeur vers une chaîne contenant la chaîne de connexion par défaut. Par défaut, cette valeur est initialisée avec la valeur NULL.

### <a name="remarks"></a>Notes

Une fois que vous avez nommé cet objet, vous pouvez ensuite appeler [Append](#append) pour enregistrer cet objet dans la collection TableDefs de la base de données. Après avoir appelé `Append`, cet objet est dans un état ouvert, et vous pouvez l’utiliser pour créer un [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objet.

Pour plus d’informations, consultez la rubrique « Méthode CreateTableDef » dans l’aide de DAO.

##  <a name="createfield"></a>  CDaoTableDef::CreateField

Appelez cette fonction membre pour ajouter un champ à la table.

```
void CreateField(
    LPCTSTR lpszName,
    short nType,
    long lSize,
    long lAttributes = 0);

void CreateField(CDaoFieldInfo& fieldinfo);
```

### <a name="parameters"></a>Paramètres

*Caractère*<br/>
Pointeur vers une expression de chaîne spécifiant le nom de ce champ.

*%nLes*<br/>
Une valeur indiquant le type de données du champ. Le paramètre peut avoir une des valeurs suivantes :

|Type|Taille (en octets)|Description|
|----------|--------------------|-----------------|
|`dbBoolean`|1 octet|BOOL|
|`dbByte`|BYTE|
|`dbInteger`|2|int|
|`dbLong`|4|long|
|`dbCurrency`|8|Devise ( [COleCurrency](../../mfc/reference/colecurrency-class.md))|
|`dbSingle`|4|float|
|`dbDouble`|8|double|
|`dbDate`|8|Date/heure ( [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|
|`dbText`|1 - 255|Texte ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbLongBinary`|0|Binaire longue (objet OLE), [CLongBinary](../../mfc/reference/clongbinary-class.md) ou [CByteArray](../../mfc/reference/cbytearray-class.md)|
|`dbMemo`|0|Mémo ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|

*lSize*<br/>
Une valeur qui indique la taille maximale, en octets, d’un champ qui contient du texte, ou la taille fixe d’un champ qui contient le texte ou des valeurs numériques. Le *lSize* paramètre est ignoré pour tous les champs de texte.

*lAttributes*<br/>
Une valeur correspondant aux caractéristiques du champ et qui peut être combinée à l’aide d’une opération de bits OR.

|Constante|Description|
|--------------|-----------------|
|`dbFixedField`|La taille du champ est fixe (valeur par défaut pour les champs numériques).|
|`dbVariableField`|La taille du champ est variable (uniquement pour les champs de texte).|
|`dbAutoIncrField`|La valeur du champ pour les nouveaux enregistrements est automatiquement incrémentée d’un entier long unique qui ne peut pas être modifié. Prise en charge uniquement pour les tables de base de données Microsoft Jet.|
|`dbUpdatableField`|La valeur du champ peut être modifiée.|
|`dbDescending`|Le champ est trié dans l’ordre décroissant (Z - A ou 0-100) ordre (s’applique uniquement à un objet de champ dans une collection de champs d’un objet Index). Si vous omettez cette constante, le champ est trié dans l’ordre croissant (A - Z ou 0 - 100) ordre (par défaut).|

*FieldInfo*<br/>
Une référence à un [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) structure.

### <a name="remarks"></a>Notes

Un `DAOField` objet (OLE) est créé et ajouté à la collection de champs de la `DAOTableDef` objet (OLE). Outre son utilisation pour l’examen des propriétés de l’objet, vous pouvez également utiliser `CDaoFieldInfo` pour construire un paramètre d’entrée pour la création de nouveaux champs dans un objet tabledef. La première version de `CreateField` est plus simple à utiliser, mais si vous souhaitez un contrôle plus précis, vous pouvez utiliser la deuxième version de `CreateField`, qui accepte un `CDaoFieldInfo` paramètre.

Si vous utilisez la version de `CreateField` qui accepte un `CDaoFieldInfo` paramètre, vous devez soigneusement définir chacun des membres suivants de la `CDaoFieldInfo` structure :

- `m_strName`

- `m_nType`

- `m_lSize`

- `m_lAttributes`

- `m_bAllowZeroLength`

Les autres membres de `CDaoFieldInfo` doit être défini sur **0**, FALSE ou une chaîne vide, comme il convient pour le membre, ou un `CDaoException` peut se produire.

Pour plus d’informations, consultez la rubrique « Méthode CreateField » dans l’aide de DAO.

##  <a name="createindex"></a>  CDaoTableDef::CreateIndex

Appelez cette fonction pour ajouter un index à une table.

```
void CreateIndex(CDaoIndexInfo& indexinfo);
```

### <a name="parameters"></a>Paramètres

*indexinfo*<br/>
Une référence à un [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) structure.

### <a name="remarks"></a>Notes

Index spécifient l’ordre des enregistrements accédé à partir des tables de base de données et ou non les enregistrements en double sont acceptés. Les index fournissent également un accès efficace aux données.

Vous n’êtes pas obligé de créer des index pour les tables, mais dans des tables volumineuses et, l’accès à un enregistrement spécifique ou la création d’un jeu d’enregistrements peut prendre un certain temps. Quant à eux, création d’index trop ralentit mise à jour, ajouter et supprimer des opérations comme tous les index sont automatiquement mis à. Considérez les facteurs lorsque vous décidez des index à créer.

Les membres suivants de la `CDaoIndexInfo` structure doit être définie :

- `m_strName` Un nom doit être fourni.

- `m_pFieldInfos` Doit pointer vers un tableau de `CDaoIndexFieldInfo` structures.

- `m_nFields` Doit spécifier le nombre de champs dans le tableau de `CDaoFieldInfo` structures.

Le restant de membres est ignoré si défini sur FALSE. En outre, le `m_lDistinctCount` membre est ignoré lors de la création de l’index.

##  <a name="deletefield"></a>  CDaoTableDef::DeleteField

Appelez cette fonction membre pour supprimer un champ et le rend inaccessible.

```
void DeleteField(LPCTSTR lpszName);
void DeleteField(int nIndex);
```

### <a name="parameters"></a>Paramètres

*Caractère*<br/>
Pointeur vers une expression de chaîne qui est le nom d’un champ existant.

*nIndex*<br/>
L’index du champ dans base zéro collection de champs de la table, pour la recherche par index.

### <a name="remarks"></a>Notes

Vous pouvez utiliser cette fonction membre sur un nouvel objet qui n’a pas été ajouté à la base de données ou lorsque [CanUpdate](#canupdate) retourne différente de zéro.

Pour plus d’informations, consultez la rubrique « Supprimer la méthode » dans l’aide de DAO.

##  <a name="deleteindex"></a>  CDaoTableDef::DeleteIndex

Appelez cette fonction membre pour supprimer un index dans une table sous-jacente.

```
void DeleteIndex(LPCTSTR lpszName);
void DeleteIndex(int nIndex);
```

### <a name="parameters"></a>Paramètres

*Caractère*<br/>
Pointeur vers une expression de chaîne qui est le nom d’un index existant.

*nIndex*<br/>
Index de tableau de l’objet d’index dans TableDefs collection de base zéro la base de données pour la recherche par index.

### <a name="remarks"></a>Notes

Vous pouvez utiliser cette fonction membre sur un nouvel objet qui n’a pas été ajouté à la base de données ou lorsque [CanUpdate](#canupdate) retourne différente de zéro.

Pour plus d’informations, consultez la rubrique « Supprimer la méthode » dans l’aide de DAO.

##  <a name="getattributes"></a>  CDaoTableDef::GetAttributes

Pour un `CDaoTableDef` objet, la valeur de retour spécifie les caractéristiques de la table représentée par le `CDaoTableDef` de l’objet et peut être une somme de ces constantes :

```
long GetAttributes();
```

### <a name="return-value"></a>Valeur de retour

Retourne une valeur qui indique une ou plusieurs caractéristiques d’un `CDaoTableDef` objet.

### <a name="remarks"></a>Notes

|Constante|Description|
|--------------|-----------------|
|`dbAttachExclusive`|Pour les bases de données qui utilisent le moteur de base de données Microsoft Jet, indique la table est une table attachée ouverte pour une utilisation exclusive.|
|`dbAttachSavePWD`|Pour les bases de données qui utilisent le moteur de base de données Microsoft Jet, indique que l’ID utilisateur et le mot de passe pour la table jointe sont enregistrées avec les informations de connexion.|
|`dbSystemObject`|Indique la table est une table système fournie par le moteur de base de données Microsoft Jet.|
|`dbHiddenObject`|Indique la table est une table masquée fournie par le moteur de base de données Microsoft Jet.|
|`dbAttachedTable`|Indique la table est une table jointe à partir d’une base de données non-ODBC, comme une base de données Paradox.|
|`dbAttachedODBC`|Indique la table est une table jointe à partir d’une base de données ODBC, telles que Microsoft SQL Server.|

Une table système est une table créée par le moteur de base de données Microsoft Jet pour contenir des informations internes différents.

Une table masquée est une table créée pour une utilisation temporaire par le moteur de base de données Microsoft Jet.

Pour plus d’informations, consultez la rubrique « Propriété des attributs » dans l’aide de DAO.

##  <a name="getconnect"></a>  CDaoTableDef::GetConnect

Appelez cette fonction membre pour obtenir la chaîne de connexion pour une source de données.

```
CString GetConnect();
```

### <a name="return-value"></a>Valeur de retour

Un `CString` objet contenant le type de chemin d’accès et de la base de données pour la table.

### <a name="remarks"></a>Notes

Pour un `CDaoTableDef` objet qui représente une table attachée, le `CString` objet se compose d’une ou deux parties (un spécificateur de type de base de données et un chemin d’accès à la base de données).

Le chemin d’accès comme indiqué dans le tableau ci-dessous est le chemin d’accès complet du répertoire contenant les fichiers de base de données et doit être précédé par l’identificateur « base de données = ». Dans certains cas (comme les bases de données avec Microsoft Jet et Microsoft Excel), un nom de fichier spécifique est incluse dans l’argument de chemin d’accès de base de données.

Le tableau dans [CDaoTableDef::SetConnect](#setconnect) présente les types de la base de données et leurs spécificateurs de base de données correspondante et les chemins d’accès :

Pour les tables de base de base de données Microsoft Jet, le spécificateur est une chaîne vide ( » »).

Si un mot de passe est requise mais non fournie, le pilote ODBC affiche une connexion boîte de dialogue la première fois une table est accessible et à nouveau si la connexion est fermée et rouverte. Si une table attachée a le `dbAttachSavePWD` attribut, l’invite de connexion n’apparaîtra pas lors de la réouverture de la table.

Pour plus d’informations, consultez la rubrique « Se connecter, propriété » dans l’aide de DAO.

##  <a name="getdatecreated"></a>  CDaoTableDef::GetDateCreated

Appelez cette fonction pour déterminer la date et l’heure de la table sous-jacente la `CDaoTableDef` objet a été créé.

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>Valeur de retour

Une valeur qui contient la date et l’heure de la création de la table sous-jacente la `CDaoTableDef` objet.

### <a name="remarks"></a>Notes

Les paramètres de date et d’heure sont dérivés de l’ordinateur sur lequel la table de base a été créée ou mises à jour. Dans un environnement multi-utilisateur, les utilisateurs doivent obtenir ces paramètres directement depuis le serveur de fichiers afin d’éviter des incohérences ; Autrement dit, tous les clients doivent utiliser une source de temps « standard » — par exemple, à un seul serveur.

Pour plus d’informations, consultez la rubrique « DateCreated, LastUpdated propriétés » dans l’aide de DAO.

##  <a name="getdatelastupdated"></a>  CDaoTableDef::GetDateLastUpdated

Appelez cette fonction pour déterminer la date et l’heure de la table sous-jacente la `CDaoTableDef` objet a été modifié.

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>Valeur de retour

Une valeur qui contient la date et l’heure de la table sous-jacente la `CDaoTableDef` objet a été modifié.

### <a name="remarks"></a>Notes

Les paramètres de date et d’heure sont dérivés de l’ordinateur sur lequel la table de base a été créée ou mises à jour. Dans un environnement multi-utilisateur, les utilisateurs doivent obtenir ces paramètres directement depuis le serveur de fichiers afin d’éviter des incohérences ; Autrement dit, tous les clients doivent utiliser une source de temps « standard » — par exemple, à un seul serveur.

Pour plus d’informations, consultez la rubrique « DateCreated, LastUpdated propriétés » dans l’aide de DAO.

##  <a name="getfieldcount"></a>  CDaoTableDef::GetFieldCount

Appelez cette fonction membre pour récupérer le nombre de champs définis dans la table.

```
short GetFieldCount();
```

### <a name="return-value"></a>Valeur de retour

Le nombre de champs dans la table.

### <a name="remarks"></a>Notes

Si sa valeur est 0, il n’existe aucun objet dans la collection.

Pour plus d’informations, consultez la rubrique « Propriété Count » dans l’aide de DAO.

##  <a name="getfieldinfo"></a>  CDaoTableDef::GetFieldInfo

Appelez cette fonction membre pour obtenir les différents types d’informations sur un champ défini dans cet objet.

```
void GetFieldInfo(
    int nIndex,
    CDaoFieldInfo& fieldinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetFieldInfo(
    LPCTSTR lpszName,
    CDaoFieldInfo& fieldinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
L’index de l’objet de champ dans base zéro collection de champs de la table, pour la recherche par index.

*FieldInfo*<br/>
Une référence à un [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) structure.

*dwInfoOptions*<br/>
Options qui spécifient les informations sur le champ à extraire. Les options disponibles sont répertoriées ici, ainsi que leur cause la fonction retourne :

- `AFX_DAO_PRIMARY_INFO` (Valeur par défaut) Nom, Type, taille, les attributs. Utilisez cette option pour meilleures performances.

- `AFX_DAO_SECONDARY_INFO` Informations primaire, ainsi que : Ordinal, obligatoire, permettre de Position zéro Table de Source de nom étrangère, champ Source, de longueur, ordre de classement,

- `AFX_DAO_ALL_INFO` Informations primaires et secondaires, ainsi que : règle de Validation, le texte de Validation, la valeur par défaut

*Caractère*<br/>
Un pointeur vers le nom de l’objet de champ, pour la recherche par nom. Le nom est une chaîne contenant jusqu'à 64 caractères qui identifie de façon unique le champ.

### <a name="remarks"></a>Notes

Une version de la fonction vous permet de rechercher un champ par index. L’autre version vous permet de rechercher un champ par nom.

Pour obtenir une description des informations retournées, consultez le [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) structure. Cette structure a des membres qui correspondent aux éléments d’informations répertoriées ci-dessus dans la description de *dwInfoOptions*. Lorsque vous demandez des informations à un niveau, vous obtenez des informations sur n’importe quel préalable des niveaux.

Pour plus d’informations, consultez la rubrique « Propriété des attributs » dans l’aide de DAO.

##  <a name="getindexcount"></a>  CDaoTableDef::GetIndexCount

Appelez cette fonction membre pour obtenir le numéro d’index pour une table.

```
short GetIndexCount();
```

### <a name="return-value"></a>Valeur de retour

Le nombre d’index pour la table.

### <a name="remarks"></a>Notes

Si sa valeur est 0, cela signifie qu’il n’y a aucun index dans la collection.

Pour plus d’informations, consultez la rubrique « Propriété Count » dans l’aide de DAO.

##  <a name="getindexinfo"></a>  CDaoTableDef::GetIndexInfo

Appelez cette fonction membre pour obtenir les différents types d’informations sur un index défini dans cet objet.

```
void GetIndexInfo(
    int nIndex,
    CDaoIndexInfo& indexinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetIndexInfo(
    LPCTSTR lpszName,
    CDaoIndexInfo& indexinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Paramètres

*nIndex*<br/>
L’index numérique de l’objet d’Index dans base zéro collection d’index de la table, pour la recherche par sa position dans la collection.

*indexinfo*<br/>
Une référence à un [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) structure.

*dwInfoOptions*<br/>
Options qui spécifient les informations sur l’index à récupérer. Les options disponibles sont répertoriées ici, ainsi que leur cause la fonction retourne :

- `AFX_DAO_PRIMARY_INFO` Champs de noms, les informations de champ. Utilisez cette option pour meilleures performances.

- `AFX_DAO_SECONDARY_INFO` Informations primaire, ainsi que : principal, Unique, Clustered, ignorer les valeurs NULL, obligatoires, étranger

- `AFX_DAO_ALL_INFO` Informations primaires et secondaires, ainsi que : comptage de valeurs

*Caractère*<br/>
Un pointeur vers le nom de l’objet index, pour la recherche par nom.

### <a name="remarks"></a>Notes

Une version de la fonction vous permet de rechercher un index par sa position dans la collection. L’autre version vous permet de rechercher un index par nom.

Pour obtenir une description des informations retournées, consultez le [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) structure. Cette structure a des membres qui correspondent aux éléments d’informations répertoriées ci-dessus dans la description de *dwInfoOptions*. Lorsque vous demandez des informations à un niveau, vous obtenez des informations sur n’importe quel préalable des niveaux.

Pour plus d’informations, consultez la rubrique « Propriété des attributs » dans l’aide de DAO.

##  <a name="getname"></a>  CDaoTableDef::GetName

Appelez cette fonction membre pour obtenir le nom défini par l’utilisateur de la table sous-jacente.

```
CString GetName();
```

### <a name="return-value"></a>Valeur de retour

Un nom défini par l’utilisateur pour une table.

### <a name="remarks"></a>Notes

Ce nom commence par une lettre et peut contenir un maximum de 64 caractères. Il peut inclure des nombres et caractères de trait de soulignement mais ne peut pas inclure de signes de ponctuation ou d’espaces.

Pour plus d’informations, consultez la rubrique « Propriété de nom » dans l’aide de DAO.

##  <a name="getrecordcount"></a>  CDaoTableDef::GetRecordCount

Appelez cette fonction membre pour savoir combien d’enregistrements est dans un `CDaoTableDef` objet.

```
long GetRecordCount();
```

### <a name="return-value"></a>Valeur de retour

Le nombre d’enregistrements auquel accédé dans un objet tabledef.

### <a name="remarks"></a>Notes

Appel `GetRecordCount` pour un type de table `CDaoTableDef` objet reflète le nombre approximatif d’enregistrements dans la table et n’est affecté immédiatement que les enregistrements de la table sont ajoutés et supprimés. Restauration des transactions seront affiche en tant que partie du nombre d’enregistrements jusqu'à ce que vous appeliez [CDaoWorkSpace::CompactDatabase](../../mfc/reference/cdaoworkspace-class.md#compactdatabase). Un `CDaoTableDef` objet sans enregistrements a un paramètre de propriété de nombre d’enregistrements de 0. Lorsque vous travaillez avec des tables jointes ou les bases de données ODBC, `GetRecordCount` retourne toujours -1.

Pour plus d’informations, consultez la rubrique « RecordCount, propriété » dans l’aide de DAO.

##  <a name="getsourcetablename"></a>  CDaoTableDef::GetSourceTableName

Appelez cette fonction membre pour récupérer le nom d’une table jointe dans une base de données source.

```
CString GetSourceTableName();
```

### <a name="return-value"></a>Valeur de retour

Un `CString` objet qui spécifie le nom de la source d’une table attachée, ou une chaîne vide si une table de données en mode natif.

### <a name="remarks"></a>Notes

Une table attachée est une table dans une autre base de données lié à une base de données Microsoft Jet. Données pour les tables jointes restent dans la base de données externe, où il peut être manipulé par d’autres applications.

Pour plus d’informations, consultez la rubrique « Propriété %{SourceTableName/} » dans l’aide de DAO.

##  <a name="getvalidationrule"></a>  CDaoTableDef::GetValidationRule

Appelez cette fonction membre pour récupérer la règle de validation pour un objet tabledef.

```
CString GetValidationRule();
```

### <a name="return-value"></a>Valeur de retour

Un `CString` objet qui valide les données dans un champ comme il est modifié ou ajouté à une table.

### <a name="remarks"></a>Notes

Règles de validation sont utilisés dans le cadre des opérations de mise à jour. Si un objet tabledef contient une règle de validation, mises à jour de ce tabledef doivent correspondre à des critères prédéfinis avant que les données sont modifiées. Si la modification ne correspond pas les critères, une exception contenant la valeur de [GetValidationText](#getvalidationtext) est levée. Pour un `CDaoTableDef` de l’objet, cela `CString` est en lecture seule pour une lecture/écriture pour une table de base et une table jointe.

Pour plus d’informations, consultez la rubrique « Propriété ValidationRule » dans l’aide de DAO.

##  <a name="getvalidationtext"></a>  CDaoTableDef::GetValidationText

Appelez cette fonction pour récupérer la chaîne à afficher lorsqu’un utilisateur entre des données qui ne correspond pas à la règle de validation.

```
CString GetValidationText();
```

### <a name="return-value"></a>Valeur de retour

Un `CString` objet qui spécifie le texte affiché si l’utilisateur entre des données qui ne correspond pas à la règle de validation.

### <a name="remarks"></a>Notes

Pour un `CDaoTableDef` de l’objet, cela `CString` est en lecture seule pour une lecture/écriture pour une table de base et une table jointe.

Pour plus d’informations, consultez la rubrique « Propriété ValidationRule » dans l’aide de DAO.

##  <a name="isopen"></a>  CDaoTableDef::IsOpen

Appelez cette fonction membre pour déterminer si le `CDaoTableDef` objet est actuellement ouvert.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro si le `CDaoTableDef` objet est ouvert ; sinon, 0.

### <a name="remarks"></a>Notes

##  <a name="m_pdatabase"></a>  CDaoTableDef::m_pDatabase

Contient un pointeur vers le [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) objet pour cette table.

### <a name="remarks"></a>Notes

##  <a name="m_pdaotabledef"></a>  CDaoTableDef::m_pDAOTableDef

Contient un pointeur vers l’interface OLE pour DAO tabledef objet sous-jacent le `CDaoTableDef` objet.

### <a name="remarks"></a>Notes

Utilisez ce pointeur si vous avez besoin d’accéder à l’interface DAO directement.

##  <a name="open"></a>  CDaoTableDef::Open

Appel cette fonction membre pour ouvrir un objet tabledef précédemment enregistrée dans la base de données du regroupement de TableDef.

```
virtual void Open(LPCTSTR lpszName);
```

### <a name="parameters"></a>Paramètres

*Caractère*<br/>
Un pointeur vers une chaîne qui spécifie un nom de table.

### <a name="remarks"></a>Notes

##  <a name="refreshlink"></a>  CDaoTableDef::RefreshLink

Appelez cette fonction membre pour mettre à jour les informations de connexion pour une table attachée.

```
void RefreshLink();
```

### <a name="remarks"></a>Notes

Vous modifiez les informations de connexion pour une table jointe en appelant [SetConnect](#setconnect) sur correspondant `CDaoTableDef` objet, puis en utilisant le `RefreshLink` fonction membre à mettre à jour les informations. Lorsque vous appelez `RefreshLink`, propriétés de la table jointe ne sont pas modifiées.

Pour forcer le texte modifié informations de connexion prenne effet, les ouvertures [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) objets selon cette tabledef doivent être fermés.

Pour plus d’informations, consultez la rubrique « Méthode RefreshLink » dans l’aide de DAO.

##  <a name="setattributes"></a>  CDaoTableDef::SetAttributes

Définit une valeur qui indique une ou plusieurs caractéristiques d’un `CDaoTableDef` objet.

```
void SetAttributes(long lAttributes);
```

### <a name="parameters"></a>Paramètres

*lAttributes*<br/>
Caractéristiques de la table représentée par le `CDaoTableDef` de l’objet et peut être une somme de ces constantes :

|Constante|Description|
|--------------|-----------------|
|`dbAttachExclusive`|Pour les bases de données qui utilisent le moteur de base de données Microsoft Jet, indique la table est une table attachée ouverte pour une utilisation exclusive.|
|`dbAttachSavePWD`|Pour les bases de données qui utilisent le moteur de base de données Microsoft Jet, indique que l’ID utilisateur et le mot de passe pour la table jointe sont enregistrées avec les informations de connexion.|
|`dbSystemObject`|Indique la table est une table système fournie par le moteur de base de données Microsoft Jet.|
|`dbHiddenObject`|Indique la table est une table masquée fournie par le moteur de base de données Microsoft Jet.|

### <a name="remarks"></a>Notes

Lorsque vous définissez plusieurs attributs, vous pouvez les combiner en additionnant les constantes appropriées à l’aide de l’opérateur OR au niveau du bit. Paramètre `dbAttachExclusive` sur une table non attachée génère une exception. Combinant les valeurs suivantes également générer une exception :

- **dbAttachExclusive &#124; dbAttachedODBC**

- **dbAttachSavePWD &#124; dbAttachedTable**

Pour plus d’informations, consultez la rubrique « Propriété des attributs » dans l’aide de DAO.

##  <a name="setconnect"></a>  CDaoTableDef::SetConnect

Pour un `CDaoTableDef` objet qui représente une table attachée, l’objet de chaîne se compose d’une ou deux parties (un spécificateur de type de base de données et un chemin d’accès à la base de données).

```
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>Paramètres

*lpszConnect*<br/>
Pointeur vers une expression de chaîne qui spécifie des paramètres supplémentaires à transmettre à ODBC ou pilotes ISAM installables.

### <a name="remarks"></a>Notes

Le chemin d’accès comme indiqué dans le tableau ci-dessous est le chemin d’accès complet du répertoire contenant les fichiers de base de données et doit être précédé par l’identificateur « base de données = ». Dans certains cas (comme les bases de données avec Microsoft Jet et Microsoft Excel), un nom de fichier spécifique est incluse dans l’argument de chemin d’accès de base de données.

> [!NOTE]
>  N’incluez pas d’espace blanc autour du signe égal dans les instructions de chemin d’accès sous la forme « base de données = lecteur :\\\path ». Cela entraîne une exception est levée et l’échec de la connexion.

Le tableau suivant présente les types de base de données possibles et leurs spécificateurs de base de données correspondante et leurs chemins :

|Type de base de données|Spécificateur|Chemin d’accès|
|-------------------|---------------|----------|
|Base de données en utilisant le moteur de base de données Jet|"[ `database`];"|« `drive`:\\\ *chemin d’accès*\\\ *filename*. MDB »|
|dBASE III|« dBASE III ; »|« `drive`:\\\ *chemin d’accès*»|
|dBASE IV|« dBASE IV ; »|« `drive`:\\\ *chemin d’accès*»|
|dBASE 5|« dBASE 5.0 ; »|« `drive`:\\\ *chemin d’accès*»|
|Paradox 3.x|« Paradox 3.x ; »|« `drive`:\\\ *chemin d’accès*»|
|Paradox 4.x|« Paradox 4.x ; »|« `drive`:\\\ *chemin d’accès*»|
|Paradox 5.x|« Paradox 5.x ; »|« `drive`:\\\ *chemin d’accès*»|
|Excel 3.0|« Excel 3.0 ; »|« `drive`:\\\ *chemin d’accès*\\\ *filename*. XLS »|
|Excel 4.0|« Excel 4.0 ; »|« `drive`:\\\ *chemin d’accès*\\\ *filename*. XLS »|
|Excel 5.0 ou Excel 95|« Excel 5.0 ; »|« `drive`:\\\ *chemin d’accès*\\\ *filename*. XLS »|
|Excel 97|« Excel 8.0 ; »|« `drive`:\\\ *chemin d’accès*\ *filename*. XLS »|
|Importation de HTML|« Importation HTML ; »|« `drive`:\\\ *chemin d’accès*\ *filename*»|
|Exportation HTML|« Export HTML ; »|« `drive`:\\\ *chemin d’accès*»|
|Texte|« Text » ;|« lecteur :\\\path »|
|ODBC|« ODBC ; Base de données = `database`; UID = *utilisateur*; PWD = *mot de passe*; DSN = *datasourcename ;* LOGINTIMEOUT = *secondes ;*» (Il peut s’agir d’une chaîne de connexion complète pour tous les serveurs ; il est juste un exemple. Il est très important de ne pas avoir des espaces entre les paramètres.)|Aucun.|
|Exchange|« Exchange ;<br /><br /> MAPILEVEL = *folderpath*;<br /><br /> [TABLETYPE = {0 &AMP;#124; 1} ;]<br /><br /> [Profil = *profil*;]<br /><br /> [PWD = *mot de passe*;]<br /><br /> [BASE DE DONNÉES = `database`;] »|*« lecteur*:\\\ *chemin d’accès*\\\ *filename*. MDB »|

> [!NOTE]
>  Btrieve n’est plus pris en charge à compter de DAO 3.5.

Vous devez utiliser une double barre oblique inverse (\\\\) dans les chaînes de connexion. Si vous avez modifié les propriétés d’une connexion existante à l’aide `SetConnect`, vous devez appeler par la suite [RefreshLink](#refreshlink). Si vous initialisez les propriétés de connexion à l’aide de `SetConnect`, vous avez besoin de ne pas appeler `RefreshLink`, mais si vous décidez de le faire, ajoutez tout d’abord à cet objet.

Si un mot de passe est requise mais non fournie, le pilote ODBC affiche une connexion boîte de dialogue la première fois une table est accessible et à nouveau si la connexion est fermée et rouverte.

Vous pouvez définir la chaîne de connexion pour un `CDaoTableDef` objet en fournissant un argument de source pour le `Create` fonction membre. Vous pouvez vérifier le paramètre pour déterminer le type, un chemin d’accès, une ID d’utilisateur, un mot de passe ou une source de données ODBC de la base de données. Pour plus d’informations, consultez la documentation relative au pilote.

Pour plus d’informations, consultez la rubrique « Se connecter, propriété » dans l’aide de DAO.

##  <a name="setname"></a>  CDaoTableDef::SetName

Appelez cette fonction membre pour définir un nom défini par l’utilisateur pour une table.

```
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>Paramètres

*Caractère*<br/>
Pointeur vers une expression de chaîne qui spécifie un nom pour une table.

### <a name="remarks"></a>Notes

Le nom doit commencer par une lettre et peut contenir un maximum de 64 caractères. Il peut inclure des nombres et caractères de trait de soulignement mais ne peut pas inclure de signes de ponctuation ou d’espaces.

Pour plus d’informations, consultez la rubrique « Propriété de nom » dans l’aide de DAO.

##  <a name="setsourcetablename"></a>  CDaoTableDef::SetSourceTableName

Appelez cette fonction membre pour spécifier le nom d’une table attachée ou le nom de la table de base sur lequel le `CDaoTableDef` objet est basé, telle qu’elle existe dans la source d’origine des données.

```
void SetSourceTableName(LPCTSTR lpszSrcTableName);
```

### <a name="parameters"></a>Paramètres

*lpszSrcTableName*<br/>
Pointeur vers une expression de chaîne qui spécifie un nom de table dans la base de données externe. Pour une table de base, le paramètre est une chaîne vide ( » »).

### <a name="remarks"></a>Notes

Vous devez ensuite appeler [RefreshLink](#refreshlink). Cette propriété est vide pour une table de base et la lecture/écriture pour une table attachée ou un objet ne pas ajouté à une collection.

Pour plus d’informations, consultez la rubrique « Propriété %{SourceTableName/} » dans l’aide de DAO.

##  <a name="setvalidationrule"></a>  CDaoTableDef::SetValidationRule

Appelez cette fonction membre pour définir une règle de validation pour un objet tabledef.

```
void SetValidationRule(LPCTSTR lpszValidationRule);
```

### <a name="parameters"></a>Paramètres

*lpszValidationRule*<br/>
Pointeur vers une expression de chaîne qui valide une opération.

### <a name="remarks"></a>Notes

Règles de validation sont utilisés dans le cadre des opérations de mise à jour. Si un objet tabledef contient une règle de validation, mises à jour de ce tabledef doivent correspondre à des critères prédéfinis avant que les données sont modifiées. Si la modification ne correspond pas les critères, une exception contenant le texte de [GetValidationText](#getvalidationtext) s’affiche.

La validation est pris en charge uniquement pour les bases de données qui utilisent le moteur de base de données Microsoft Jet. L’expression ne peut pas faire référence à des fonctions définies par l’utilisateur, des fonctions d’agrégation domaine, des fonctions d’agrégation SQL ou des requêtes. Une règle de validation pour un `CDaoTableDef` objet peut faire référence à plusieurs champs dans cet objet.

Par exemple, pour les champs nommés *hire_date* et *termination_date*, une règle de validation peut être :

[!code-cpp[NVC_MFCDatabase#34](../../mfc/codesnippet/cpp/cdaotabledef-class_1.cpp)]

Pour plus d’informations, consultez la rubrique « Propriété ValidationRule » dans l’aide de DAO.

##  <a name="setvalidationtext"></a>  CDaoTableDef::SetValidationText

Appelez cette fonction membre pour définir le texte d’exception d’une règle de validation pour un `CDaoTableDef` objet avec une table de base sous-jacente pris en charge par le moteur de base de données Microsoft Jet.

```
void SetValidationText(LPCTSTR lpszValidationText);
```

### <a name="parameters"></a>Paramètres

*lpszValidationText*<br/>
Un pointeur vers une expression de chaîne qui spécifie le texte affiché si vous avez entré des données n’est pas valide.

### <a name="remarks"></a>Notes

Vous ne pouvez pas définir le texte de validation d’une table attachée.

Pour plus d’informations, consultez la rubrique « Propriété ValidationRule » dans l’aide de DAO.

## <a name="see-also"></a>Voir aussi

[CObject, classe](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CDaoDatabase, classe](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoRecordset, classe](../../mfc/reference/cdaorecordset-class.md)
