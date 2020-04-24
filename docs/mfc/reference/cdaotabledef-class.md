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
ms.openlocfilehash: adc31ccbf2be34aa1df1fa56111d1990701a6329
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754692"
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
|[CDaoTableDef::CanUpdate](#canupdate)|Retourne nonzero si le tableau peut être mis à jour (vous pouvez modifier la définition des champs ou des propriétés de table).|
|[CDaoTableDef::Fermer](#close)|Ferme un tableau ouvert.|
|[CDaoTableDef::Créer](#create)|Crée une table qui peut être ajoutée à la base de données à [l’aide de l’annexe](#append).|
|[CDaoTableDef::CreateField](#createfield)|Appelé à créer un champ pour une table.|
|[CDaoTableDef::CreateIndex](#createindex)|Appelé à créer un index pour une table.|
|[CDaoTableDef::DeleteField](#deletefield)|Appelé pour supprimer un champ d’une table.|
|[CDaoTableDef::DeleteIndex](#deleteindex)|Appelé à supprimer un index d’une table.|
|[CDaoTableDef::GetAttributes](#getattributes)|Retourne une valeur qui indique une `CDaoTableDef` ou plusieurs caractéristiques d’un objet.|
|[CDaoTableDef::GetConnect](#getconnect)|Retourne une valeur qui fournit des informations sur la source d’un tableau.|
|[CDaoTableDef::GetDateCreated](#getdatecreated)|Retourne la date et l’heure de la table de base sous-jacente à un `CDaoTableDef` objet a été créée.|
|[CDaoTableDef::GetDateLastUpdated](#getdatelastupdated)|Retourne la date et l’heure du changement le plus récent apporté à la conception de la table de base.|
|[CDaoTableDef::GetFieldCount](#getfieldcount)|Retourne une valeur qui représente le nombre de champs dans le tableau.|
|[CDaoTableDef::GetFieldInfo](#getfieldinfo)|Renvoie des types spécifiques d’informations sur les champs dans le tableau.|
|[CDaoTableDef::GetIndexCount](#getindexcount)|Retourne le nombre d’index pour le tableau.|
|[CDaoTableDef::GetIndexInfo](#getindexinfo)|Renvoie des types spécifiques d’informations sur les index pour le tableau.|
|[CDaoTableDef::GetName](#getname)|Retourne le nom défini par l’utilisateur de la table.|
|[CDaoTableDef::GetRecordCount](#getrecordcount)|Retourne le nombre d’enregistrements dans le tableau.|
|[CDaoTableDef::GetSourceTableName](#getsourcetablename)|Retourne une valeur qui spécifie le nom du tableau ci-joint dans la base de données source.|
|[CDaoTableDef::GetValidationRule](#getvalidationrule)|Retourne une valeur qui valide les données dans un champ tel qu’il est modifié ou ajouté à un tableau.|
|[CDaoTableDef::GetValidationText](#getvalidationtext)|Retourne une valeur qui spécifie le texte du message que votre application affiche si la valeur d’un objet Field ne satisfait pas à la règle de validation spécifiée.|
|[CDaoTableDef::IsOpen](#isopen)|Retourne nonzero si la table est ouverte.|
|[CDaoTableDef::Ouvert](#open)|Ouvre un dépôt existant stocké dans la collection De tableDef de la base de données.|
|[CDaoTableDef::RefreshLink](#refreshlink)|Mise à jour des informations de connexion pour une table jointe.|
|[CDaoTableDef::SetAttributes](#setattributes)|Définit une valeur qui indique une `CDaoTableDef` ou plusieurs caractéristiques d’un objet.|
|[CDaoTableDef::SetConnect](#setconnect)|Définit une valeur qui fournit des informations sur la source d’une table.|
|[CDaoTableDef::SetName](#setname)|Définit le nom de la table.|
|[CDaoTableDef::SetSourceTableName](#setsourcetablename)|Définit une valeur qui spécifie le nom d’une table jointe dans la base de données source.|
|[CDaoTableDef::SetValidationRule](#setvalidationrule)|Définit une valeur qui valide les données dans un champ tel qu’elles sont modifiées ou ajoutées à une table.|
|[CDaoTableDef::SetValidationText](#setvalidationtext)|Définit une valeur qui spécifie le texte du message que votre application affiche si la valeur d’un objet Field ne satisfait pas à la règle de validation spécifiée.|

### <a name="public-data-members"></a>Membres de données publics

|Nom|Description|
|----------|-----------------|
|[CDaoTableDef::m_pDAOTableDef](#m_pdaotabledef)|Un pointeur à l’interface DAO sous-jacente à l’objet tabledef.|
|[CDaoTableDef::m_pDatabase](#m_pdatabase)|Base de données source pour ce tableau.|

## <a name="remarks"></a>Notes

Chaque objet de base de données DAO conserve une collection, appelée TableDefs, qui contient tous les objets de dépôt DAO enregistrés.

Vous manipulez une `CDaoTableDef` définition de table à l’aide d’un objet. Vous pouvez par exemple :

- Examinez la structure de champ et d’index de n’importe quelle table locale, jointe ou externe dans une base de données.

- Appelez `SetConnect` les `SetSourceTableName` fonctions et les fonctions `RefreshLink` des membres pour les tables jointes et utilisez la fonction membre pour mettre à jour les connexions aux tables jointes.

- Appelez `CanUpdate` la fonction membre pour déterminer si vous pouvez modifier les définitions de champ dans le tableau.

- Obtenez ou définissez `GetValidationRule` des `SetValidationRule`conditions `GetValidationText` de `SetValidationText` validation à l’aide des fonctions et des fonctions des membres.

- Utilisez `Open` la fonction membre pour créer un objet de type `CDaoRecordset` table, dynaset ou instantané.

    > [!NOTE]
    >  Les classes de base de données DAO sont distinctes des classes de base de données MFC basées sur la connectivité open Database (ODBC). Tous les noms de classe de base de données DAO ont le préfixe "CDao". Vous pouvez toujours accéder aux sources de données ODBC avec les classes DAO; les classes DAO offrent généralement des capacités supérieures parce qu’elles sont spécifiques au moteur de base de données Microsoft Jet.

### <a name="to-use-tabledef-objects-either-to-work-with-an-existing-table-or-to-create-a-new-table"></a>Utiliser des objets de table pour travailler avec une table existante ou pour créer une nouvelle table

1. Dans tous les cas, construisez d’abord un `CDaoTableDef` objet, fournissant un pointeur à un objet [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) auquel appartient la table.

1. Ensuite, faites ce qui suit, en fonction de ce que vous voulez:

   - Pour utiliser une table enregistrée existante, appelez la fonction de membre [Open](#open) de l’objet de dépôt, en fournissant le nom de la table enregistrée.

   - Pour créer une nouvelle table, appelez la fonction de membre Create de l’objet [de](#create) dépôt, en fournissant le nom de la table. Appelez [CreateField](#createfield) et [CreateIndex](#createindex) pour ajouter des champs et des index à la table.

   - Appelez [l’annexe](#append) pour enregistrer la table en l’appendice à la collection TableDefs de la base de données. `Create`met le dépôt dans un état ouvert, donc après avoir appelé `Create` vous n’appelez `Open`pas .

        > [!TIP]
        >  La façon la plus simple de créer des tables enregistrées est de les créer et de les stocker dans votre base de données à l’aide de Microsoft Access. Ensuite, vous pouvez les ouvrir et les utiliser dans votre code MFC.

Pour utiliser l’objet tabledef que vous avez `CDaoRecordset` ouvert ou créé, créez et ouvrez un objet, en spécifiant le nom du code de dépôt avec une `dbOpenTable` valeur dans le paramètre *nOpenType.*

Pour utiliser un objet tabledef pour créer un `CDaoRecordset` objet, vous créez ou ouvrez généralement un code de table tel que décrit ci-dessus, puis construisez un objet de la composition des enregistrements, en passant un pointeur sur votre objet tabledef lorsque vous appelez [CDaoRecordset : : Ouvrez](../../mfc/reference/cdaorecordset-class.md#open). Le dépôt que vous passez doit être en état d’ouverture. Pour plus d’informations, voir classe [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

Lorsque vous avez terminé à l’aide d’un objet tabledef, appelez sa fonction de membre [Close](../../mfc/reference/cdaorecordset-class.md#close) ; puis détruire l’objet de dépôt.

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CDaoTableDef`

## <a name="requirements"></a>Spécifications

**En-tête:** afxdao.h

## <a name="cdaotabledefappend"></a><a name="append"></a>CDaoTableDef::Append

Appelez cette fonction de membre après avoir appelé [Create](#create) pour créer un nouvel objet de dépôt pour enregistrer le code de dépôt dans la base de données.

```
virtual void Append();
```

### <a name="remarks"></a>Notes

La fonction annexe l’objet à la collection TableDefs de la base de données. Vous pouvez utiliser le code de dépôt comme un objet temporaire tout en le définissant en `Append`ne l’appending, mais si vous voulez l’enregistrer et l’utiliser, vous devez appeler .

> [!NOTE]
> Si vous tentez d’ajouter un code de dépôt anonyme (contenant une corde nulle ou vide), MFC lance une exception.

Pour plus d’informations connexes, consultez le thème « Méthode d’annexe » dans DAO Help.

## <a name="cdaotabledefcanupdate"></a><a name="canupdate"></a>CDaoTableDef::CanUpdate

Appelez cette fonction de membre pour déterminer `CDaoTableDef` si la définition du tableau sous-jacent à un objet peut être modifiée.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Valeur de retour

Nonzero si la structure de table (schéma) peut être modifiée (ajouter ou supprimer les champs et les index), sinon 0.

### <a name="remarks"></a>Notes

Par défaut, une table `CDaoTableDef` nouvellement créée sous-jacente à `CDaoTableDef` un objet peut être mise à jour, et une table jointe sous-jacente à un objet ne peut pas être mise à jour. Un `CDaoTableDef` objet peut être updatable, même si le recordet résultant n’est pas updatable.

Pour obtenir des informations connexes, consultez le thème « Propriété Updatable » dans DAO Help.

## <a name="cdaotabledefcdaotabledef"></a><a name="cdaotabledef"></a>CDaoTableDef::CDaoTableDef

Construit un objet `CDaoTableDef`.

```
CDaoTableDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>Paramètres

*base de pData*<br/>
Un pointeur vers un objet [CDaoDatabase.](../../mfc/reference/cdaodatabase-class.md)

### <a name="remarks"></a>Notes

Après avoir construit l’objet, vous devez appeler la fonction De membre [Créer](#create) ou [ouvrir.](#open) Lorsque vous avez terminé avec l’objet, vous `CDaoTableDef` devez appeler sa fonction de membre [Proche](#close) et détruire l’objet.

## <a name="cdaotabledefclose"></a><a name="close"></a>CDaoTableDef::Fermer

Appelez cette fonction de membre pour fermer et libérer l’objet de dépôt.

```
virtual void Close();
```

### <a name="remarks"></a>Notes

Habituellement, `Close`après avoir appelé , vous supprimez l’objet tabledef si elle a été allouée avec **de nouveaux**.

Vous pouvez [Open](#open) appeler Open `Close`à nouveau après avoir appelé . Cela vous permet de réutiliser l’objet de dépôt.

Pour obtenir des informations connexes, consultez le thème « Méthode de clôture » dans DAO Help.

## <a name="cdaotabledefcreate"></a><a name="create"></a>CDaoTableDef::Créer

Appelez cette fonction de membre pour créer une nouvelle table enregistrée.

```
virtual void Create(
    LPCTSTR lpszName,
    long lAttributes = 0,
    LPCTSTR lpszSrcTable = NULL,
    LPCTSTR lpszConnect = NULL);
```

### <a name="parameters"></a>Paramètres

*lpszName (en)*<br/>
Un pointeur à une chaîne contenant le nom de la table.

*lAttributes*<br/>
Une valeur correspondant aux caractéristiques de la table représentée par l’objet de dépôt. Vous pouvez utiliser le bitwise-OR pour combiner l’une des constantes suivantes:

|Constant|Description|
|--------------|-----------------|
|`dbAttachExclusive`|Pour les bases de données qui utilisent le moteur de base de données Microsoft Jet, indique que la table est une table attachée ouverte pour une utilisation exclusive.|
|`dbAttachSavePWD`|Pour les bases de données qui utilisent le moteur de base de données Microsoft Jet, indique que l’identifiant utilisateur et le mot de passe pour la table ci-jointe sont enregistrés avec les informations de connexion.|
|`dbSystemObject`|Indique que la table est une table système fournie par le moteur de base de données Microsoft Jet.|
|`dbHiddenObject`|Indique que la table est une table cachée fournie par le moteur de base de données Microsoft Jet.|

*lpszSrcTable*<br/>
Un pointeur à une chaîne contenant le nom de table source. Par défaut, cette valeur est parascée sous le titre NULL.

*lpszConnect*<br/>
Un pointeur à une chaîne contenant la chaîne de connexion par défaut. Par défaut, cette valeur est parascée sous le titre NULL.

### <a name="remarks"></a>Notes

Une fois que vous avez nommé le code de dépôt, vous pouvez ensuite appeler [Append](#append) pour enregistrer le code de dépôt dans la collection TableDefs de la base de données. Après `Append`l’appel , le code de dépôt est en état d’ouverture, et vous pouvez l’utiliser pour créer un objet [CDaoRecordset.](../../mfc/reference/cdaorecordset-class.md)

Pour plus d’informations connexes, consultez le thème "CreateTableDef Method" dans DAO Help.

## <a name="cdaotabledefcreatefield"></a><a name="createfield"></a>CDaoTableDef::CreateField

Appelez cette fonction de membre pour ajouter un champ à la table.

```cpp
void CreateField(
    LPCTSTR lpszName,
    short nType,
    long lSize,
    long lAttributes = 0);

void CreateField(CDaoFieldInfo& fieldinfo);
```

### <a name="parameters"></a>Paramètres

*lpszName (en)*<br/>
Un pointeur à une expression de chaîne spécifiant le nom de ce champ.

*nType*<br/>
Une valeur indiquant le type de données du champ. Le paramètre peut être l’une de ces valeurs :

|Type|Taille (en octets)|Description|
|----------|--------------------|-----------------|
|`dbBoolean`|1 octet|BOOL|
|`dbByte`|BYTE|
|`dbInteger`|2|int|
|`dbLong`|4|long|
|`dbCurrency`|8|Monnaie ( [COleCurrency](../../mfc/reference/colecurrency-class.md))|
|`dbSingle`|4|float|
|`dbDouble`|8|double|
|`dbDate`|8|Date/Heure ( [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|
|`dbText`|1 - 255|Texte ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbLongBinary`|0|Long Binaire (objet OLE), [CLongBinary](../../mfc/reference/clongbinary-class.md) ou [CByteArray](../../mfc/reference/cbytearray-class.md)|
|`dbMemo`|0|Mémo ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|

*lSize*<br/>
Une valeur qui indique la taille maximale, dans les octets, d’un champ qui contient du texte, ou la taille fixe d’un champ qui contient du texte ou des valeurs numériques. Le *paramètre lSize* est ignoré pour tous les champs, sauf le texte.

*lAttributes*<br/>
Une valeur correspondant aux caractéristiques du champ et qui peut être combinée à l’aide d’un bitwise-OR.

|Constant|Description|
|--------------|-----------------|
|`dbFixedField`|La taille du champ est fixe (par défaut pour les champs Numeric).|
|`dbVariableField`|La taille du champ est variable (Champs de texte seulement).|
|`dbAutoIncrField`|La valeur de champ pour les nouveaux enregistrements est automatiquement incrémentée à un intégrant long unique qui ne peut pas être changé. Seulement pris en charge pour les tables de base de données Microsoft Jet.|
|`dbUpdatableField`|La valeur du champ peut être modifiée.|
|`dbDescending`|Le champ est trié dans la descente (Z - A ou 100 - 0) commande (ne s’applique qu’à un objet Field dans une collection Fields d’un objet Index). Si vous ometez cette constante, le champ est trié dans l’ordre ascendant (A - Z ou 0 - 100) (par défaut).|

*Fieldinfo*<br/>
Une référence à une structure [CDaoFieldInfo.](../../mfc/reference/cdaofieldinfo-structure.md)

### <a name="remarks"></a>Notes

Un `DAOField` objet (OLE) est créé et annexé `DAOTableDef` à la collection Fields de l’objet (OLE). Outre son utilisation pour l’examen `CDaoFieldInfo` des propriétés de l’objet, vous pouvez également utiliser pour construire un paramètre d’entrée pour créer de nouveaux champs dans un tabledef. La première `CreateField` version de est plus simple à utiliser, mais si vous `CreateField`voulez un `CDaoFieldInfo` contrôle plus fin, vous pouvez utiliser la deuxième version de , qui prend un paramètre.

Si vous utilisez `CreateField` la version `CDaoFieldInfo` de ce qui prend un paramètre, `CDaoFieldInfo` vous devez définir soigneusement chacun des membres suivants de la structure:

- `m_strName`

- `m_nType`

- `m_lSize`

- `m_lAttributes`

- `m_bAllowZeroLength`

Les membres `CDaoFieldInfo` restants de doivent être réglés à **0**, FALSE, `CDaoException` ou une chaîne vide, le cas échéant pour le membre, ou un peut se produire.

Pour obtenir des informations connexes, consultez le thème « Méthode CreateField » dans DAO Help.

## <a name="cdaotabledefcreateindex"></a><a name="createindex"></a>CDaoTableDef::CreateIndex

Appelez cette fonction pour ajouter un index à une table.

```cpp
void CreateIndex(CDaoIndexInfo& indexinfo);
```

### <a name="parameters"></a>Paramètres

*indexinfo*<br/>
Une référence à une structure [CDaoIndexInfo.](../../mfc/reference/cdaoindexinfo-structure.md)

### <a name="remarks"></a>Notes

Les index spécifient l’ordre des enregistrements consultés à partir des tables de base de données et si les enregistrements en double sont acceptés ou non. Les indices offrent également un accès efficace aux données.

Vous n’avez pas à créer des index pour les tables, mais dans de grandes tables non indexées, l’accès à un enregistrement spécifique ou la création d’un ensemble d’enregistrements peut prendre beaucoup de temps. D’autre part, la création d’un trop grand nombre d’index ralentit les mises à jour, les appendices et les suppressions d’opérations au fur et à mesure que tous les index sont automatiquement mis à jour. Considérez ces facteurs lorsque vous décidez quels index créer.

Les membres suivants `CDaoIndexInfo` de la structure doivent être définis :

- `m_strName`Un nom doit être fourni.

- `m_pFieldInfos`Doit indiquer un `CDaoIndexFieldInfo` éventail de structures.

- `m_nFields`Doit spécifier le nombre `CDaoFieldInfo` de champs dans la gamme de structures.

Les membres restants seront ignorés s’ils sont réglés sur FALSE. En outre, `m_lDistinctCount` le membre est ignoré lors de la création de l’index.

## <a name="cdaotabledefdeletefield"></a><a name="deletefield"></a>CDaoTableDef::DeleteField

Appelez cette fonction de membre pour enlever un champ et le rendre inaccessible.

```cpp
void DeleteField(LPCTSTR lpszName);
void DeleteField(int nIndex);
```

### <a name="parameters"></a>Paramètres

*lpszName (en)*<br/>
Un pointeur à une expression de chaîne qui est le nom d’un champ existant.

*nIndex*<br/>
L’indice du champ dans la collection Fields à base zéro du tableau, pour la recherche par index.

### <a name="remarks"></a>Notes

Vous pouvez utiliser cette fonction de membre sur un nouvel objet qui n’a pas été annexé à la base de données ou lorsque [CanUpdate](#canupdate) renvoie nonzero.

Pour obtenir des informations connexes, consultez le thème « Supprimer la méthode » dans DAO Help.

## <a name="cdaotabledefdeleteindex"></a><a name="deleteindex"></a>CDaoTableDef::DeleteIndex

Appelez cette fonction de membre pour supprimer un index dans un tableau sous-jacent.

```cpp
void DeleteIndex(LPCTSTR lpszName);
void DeleteIndex(int nIndex);
```

### <a name="parameters"></a>Paramètres

*lpszName (en)*<br/>
Un pointeur à une expression de chaîne qui est le nom d’un index existant.

*nIndex*<br/>
L’indice de tableau de l’objet indiciel dans la collection TableDefs à base zéro de la base de données, pour le lookup par index.

### <a name="remarks"></a>Notes

Vous pouvez utiliser cette fonction de membre sur un nouvel objet qui n’a pas été annexé à la base de données ou lorsque [CanUpdate](#canupdate) renvoie nonzero.

Pour obtenir des informations connexes, consultez le thème « Supprimer la méthode » dans DAO Help.

## <a name="cdaotabledefgetattributes"></a><a name="getattributes"></a>CDaoTableDef::GetAttributes

Pour `CDaoTableDef` un objet, la valeur de retour spécifie les caractéristiques du tableau représenté par l’objet `CDaoTableDef` et peut être une somme de ces constantes :

```
long GetAttributes();
```

### <a name="return-value"></a>Valeur de retour

Retourne une valeur qui indique une `CDaoTableDef` ou plusieurs caractéristiques d’un objet.

### <a name="remarks"></a>Notes

|Constant|Description|
|--------------|-----------------|
|`dbAttachExclusive`|Pour les bases de données qui utilisent le moteur de base de données Microsoft Jet, indique que la table est une table attachée ouverte pour une utilisation exclusive.|
|`dbAttachSavePWD`|Pour les bases de données qui utilisent le moteur de base de données Microsoft Jet, indique que l’identifiant utilisateur et le mot de passe pour la table ci-jointe sont enregistrés avec les informations de connexion.|
|`dbSystemObject`|Indique que la table est une table système fournie par le moteur de base de données Microsoft Jet.|
|`dbHiddenObject`|Indique que la table est une table cachée fournie par le moteur de base de données Microsoft Jet.|
|`dbAttachedTable`|Indique que la table est une table jointe à partir d’une base de données non-ODBC, comme une base de données Paradox.|
|`dbAttachedODBC`|Indique que la table est une table jointe à partir d’une base de données ODBC, comme Microsoft SQL Server.|

Une table système est une table créée par le moteur de base de données Microsoft Jet pour contenir diverses informations internes.

Une table cachée est une table créée pour une utilisation temporaire par le moteur de base de données Microsoft Jet.

Pour obtenir des renseignements connexes, consultez le thème « Propriété d’attributs » dans DAO Help.

## <a name="cdaotabledefgetconnect"></a><a name="getconnect"></a>CDaoTableDef::GetConnect

Appelez cette fonction de membre pour obtenir la chaîne de connexion pour une source de données.

```
CString GetConnect();
```

### <a name="return-value"></a>Valeur de retour

Un `CString` objet contenant le chemin et le type de base de données pour la table.

### <a name="remarks"></a>Notes

Pour `CDaoTableDef` un objet qui représente `CString` une table jointe, l’objet se compose d’une ou deux parties (un spécificateur de type base de données et un chemin vers la base de données).

Le chemin indiqué dans le tableau ci-dessous est le chemin complet pour l’annuaire contenant les fichiers de base de données et doit être précédé par l’identifiant "DATABASE". Dans certains cas (comme avec les bases de données Microsoft Jet et Microsoft Excel), un nom de fichier spécifique est inclus dans l’argument de la trajectoire de base de données.

Le tableau de [CDaoTableDef::SetConnect](#setconnect) affiche les types de bases de données possibles et leurs spécifications et chemins de base de données correspondants :

Pour les tables de base de base de base Microsoft Jet, le spécificateur est une chaîne vide ("").

Si un mot de passe est requis mais non fourni, le conducteur de l’ODBC affiche une boîte de dialogue de connexion la première fois qu’une table est consultée et à nouveau si la connexion est fermée et rouverte. Si une table `dbAttachSavePWD` jointe a l’attribut, l’invite de connexion n’apparaîtra pas lorsque la table est rouverte.

Pour obtenir des informations connexes, consultez le thème « Connect Property » dans DAO Help.

## <a name="cdaotabledefgetdatecreated"></a><a name="getdatecreated"></a>CDaoTableDef::GetDateCreated

Appelez cette fonction pour déterminer la date `CDaoTableDef` et l’heure de la création du tableau sous-jacent à l’objet.

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>Valeur de retour

Une valeur contenant la date et l’heure `CDaoTableDef` de la création du tableau sous-jacent à l’objet.

### <a name="remarks"></a>Notes

Les paramètres de date et d’heure sont dérivés de l’ordinateur sur lequel la table de base a été créée ou mise à jour pour la dernière fois. Dans un environnement multi-utilisateurs, les utilisateurs doivent obtenir ces paramètres directement à partir du serveur de fichiers pour éviter les écarts; c’est-à-dire que tous les clients devraient utiliser une source de temps « standard » — peut-être à partir d’un seul serveur.

Pour plus d’informations connexes, voir le sujet "DateCreated, LastUpdated Properties" dans DAO Help.

## <a name="cdaotabledefgetdatelastupdated"></a><a name="getdatelastupdated"></a>CDaoTableDef::GetDateLastUpdated

Appelez cette fonction pour déterminer la date `CDaoTableDef` et l’heure à laquelle le tableau sous-jacent à l’objet a été mis à jour pour la dernière fois.

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>Valeur de retour

Une valeur qui contient la date `CDaoTableDef` et l’heure du tableau sous-jacent à l’objet a été mise à jour pour la dernière fois.

### <a name="remarks"></a>Notes

Les paramètres de date et d’heure sont dérivés de l’ordinateur sur lequel la table de base a été créée ou mise à jour pour la dernière fois. Dans un environnement multi-utilisateurs, les utilisateurs doivent obtenir ces paramètres directement à partir du serveur de fichiers pour éviter les écarts; c’est-à-dire que tous les clients devraient utiliser une source de temps « standard » — peut-être à partir d’un seul serveur.

Pour plus d’informations connexes, voir le sujet "DateCreated, LastUpdated Properties" dans DAO Help.

## <a name="cdaotabledefgetfieldcount"></a><a name="getfieldcount"></a>CDaoTableDef::GetFieldCount

Appelez cette fonction de membre pour récupérer le nombre de champs définis dans le tableau.

```
short GetFieldCount();
```

### <a name="return-value"></a>Valeur de retour

Le nombre de champs dans le tableau.

### <a name="remarks"></a>Notes

Si sa valeur est de 0, il n’y a pas d’objets dans la collection.

Pour obtenir des renseignements connexes, consultez le thème « Count Property » dans DAO Help.

## <a name="cdaotabledefgetfieldinfo"></a><a name="getfieldinfo"></a>CDaoTableDef::GetFieldInfo

Appelez cette fonction de membre pour obtenir divers types d’informations sur un champ défini dans le dépôt.

```cpp
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
L’index de l’objet de champ dans la collection Fields à base zéro du tableau, pour la recherche par index.

*Fieldinfo*<br/>
Une référence à une structure [CDaoFieldInfo.](../../mfc/reference/cdaofieldinfo-structure.md)

*dwInfoOptions*<br/>
Options qui spécifient les informations sur le champ à récupérer. Les options disponibles sont énumérées ici ainsi que ce qu’elles causent le retour de la fonction :

- `AFX_DAO_PRIMARY_INFO`(Par défaut) Nom, Type, Taille, Attributs. Utilisez cette option pour des performances les plus rapides.

- `AFX_DAO_SECONDARY_INFO`Informations primaires, plus: Position ordinaire, Requise, Permettre la longueur zéro, Ordonnance de collating, Nom étranger, Champ source, Tableau source

- `AFX_DAO_ALL_INFO`Informations primaires et secondaires, plus : Règle de validation, Texte de validation, Valeur par défaut

*lpszName (en)*<br/>
Un pointeur au nom de l’objet de champ, pour le lookup par nom. Le nom est une chaîne avec jusqu’à 64 caractères qui nomme uniquement le champ.

### <a name="remarks"></a>Notes

Une version de la fonction vous permet de rechercher un champ par index. L’autre version vous permet de rechercher un champ par son nom.

Pour une description de l’information retournée, voir la structure [CDaoFieldInfo.](../../mfc/reference/cdaofieldinfo-structure.md) Cette structure a des membres qui correspondent aux éléments d’information énumérés ci-dessus dans la description de *dwInfoOptions*. Lorsque vous demandez des informations à un niveau, vous obtenez des informations pour tous les niveaux antérieurs ainsi.

Pour obtenir des renseignements connexes, consultez le thème « Propriété d’attributs » dans DAO Help.

## <a name="cdaotabledefgetindexcount"></a><a name="getindexcount"></a>CDaoTableDef::GetIndexCount

Appelez cette fonction de membre pour obtenir le nombre d’index pour un tableau.

```
short GetIndexCount();
```

### <a name="return-value"></a>Valeur de retour

Le nombre d’index pour le tableau.

### <a name="remarks"></a>Notes

Si sa valeur est de 0, il n’y a pas d’indices dans la collection.

Pour obtenir des renseignements connexes, consultez le thème « Count Property » dans DAO Help.

## <a name="cdaotabledefgetindexinfo"></a><a name="getindexinfo"></a>CDaoTableDef::GetIndexInfo

Appelez cette fonction de membre pour obtenir divers types d’informations sur un index défini dans le dépôt.

```cpp
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
L’indice numérique de l’objet Index dans la collection d’indices à base de zéro du tableau, pour la recherche par sa position dans la collection.

*indexinfo*<br/>
Une référence à une structure [CDaoIndexInfo.](../../mfc/reference/cdaoindexinfo-structure.md)

*dwInfoOptions*<br/>
Options qui spécifient les informations sur l’index à récupérer. Les options disponibles sont énumérées ici ainsi que ce qu’elles causent le retour de la fonction :

- `AFX_DAO_PRIMARY_INFO`Nom, Field Info, Fields. Utilisez cette option pour des performances les plus rapides.

- `AFX_DAO_SECONDARY_INFO`Informations primaires, plus: Primaire, Unique, Clustered, Ignorer Nulls, Requis, Étranger

- `AFX_DAO_ALL_INFO`Informations primaires et secondaires, plus : Nombre distinct

*lpszName (en)*<br/>
Un pointeur sur le nom de l’objet de l’index, pour le lookup par nom.

### <a name="remarks"></a>Notes

Une version de la fonction vous permet de rechercher un index par sa position dans la collection. L’autre version vous permet de rechercher un index par nom.

Pour une description de l’information retournée, voir la structure [CDaoIndexInfo.](../../mfc/reference/cdaoindexinfo-structure.md) Cette structure a des membres qui correspondent aux éléments d’information énumérés ci-dessus dans la description de *dwInfoOptions*. Lorsque vous demandez des informations à un niveau, vous obtenez des informations pour tous les niveaux antérieurs ainsi.

Pour obtenir des renseignements connexes, consultez le thème « Propriété d’attributs » dans DAO Help.

## <a name="cdaotabledefgetname"></a><a name="getname"></a>CDaoTableDef::GetName

Appelez cette fonction de membre pour obtenir le nom défini par l’utilisateur du tableau sous-jacent.

```
CString GetName();
```

### <a name="return-value"></a>Valeur de retour

Un nom défini par l’utilisateur pour une table.

### <a name="remarks"></a>Notes

Ce nom commence par une lettre et peut contenir un maximum de 64 caractères. Il peut inclure des nombres et des personnages de souligner, mais ne peut pas inclure la ponctuation ou des espaces.

Pour obtenir des informations connexes, consultez le thème « Propriété du nom » dans DAO Help.

## <a name="cdaotabledefgetrecordcount"></a><a name="getrecordcount"></a>CDaoTableDef::GetRecordCount

Appelez cette fonction de membre pour savoir `CDaoTableDef` combien d’enregistrements sont dans un objet.

```
long GetRecordCount();
```

### <a name="return-value"></a>Valeur de retour

Nombre d’enregistrements consultés dans un objet de dépôt.

### <a name="remarks"></a>Notes

L’appel pour `GetRecordCount` `CDaoTableDef` un objet de type table reflète le nombre approximatif d’enregistrements dans le tableau et est affecté immédiatement au fur et à mesure que les enregistrements de table sont ajoutés et supprimés. Les transactions annulées apparaîtront dans le cadre du nombre d’enregistrements jusqu’à ce que vous [appeliez CDaoWorkSpace::CompactDatabase](../../mfc/reference/cdaoworkspace-class.md#compactdatabase). Un `CDaoTableDef` objet sans dossier a un nombre record de propriété de 0. Lorsque vous travaillez avec des tables `GetRecordCount` jointes ou des bases de données ODBC, retourne toujours -1.

Pour obtenir des renseignements connexes, consultez le thème « RecordCount Property » dans DAO Help.

## <a name="cdaotabledefgetsourcetablename"></a><a name="getsourcetablename"></a>CDaoTableDef::GetSourceTableName

Appelez cette fonction de membre pour récupérer le nom d’une table jointe dans une base de données source.

```
CString GetSourceTableName();
```

### <a name="return-value"></a>Valeur de retour

Un `CString` objet qui spécifie le nom source d’une table jointe, ou une chaîne vide si une table de données native.

### <a name="remarks"></a>Notes

Une table jointe est une table dans une autre base de données liée à une base de données Microsoft Jet. Les données pour les tables jointes restent dans la base de données externe, où elles peuvent être manipulées par d’autres applications.

Pour plus d’informations connexes, consultez le thème "SourceTableName Property" dans DAO Help.

## <a name="cdaotabledefgetvalidationrule"></a><a name="getvalidationrule"></a>CDaoTableDef::GetValidationRule

Appelez cette fonction de membre pour récupérer la règle de validation pour un dépôt.

```
CString GetValidationRule();
```

### <a name="return-value"></a>Valeur de retour

Un `CString` objet qui valide les données dans un champ tel qu’il est modifié ou ajouté à une table.

### <a name="remarks"></a>Notes

Les règles de validation sont utilisées dans le cadre des opérations de mise à jour. Si un dépôt contient une règle de validation, les mises à jour de ce formulaire doivent correspondre aux critères prédéterminés avant que les données ne soient modifiées. Si la modification ne correspond pas aux critères, une exception contenant la valeur de [GetValidationText](#getvalidationtext) est lancée. Pour `CDaoTableDef` un objet, il s’agit `CString` d’une lecture uniquement pour une table jointe et de lecture/écriture pour une table de base.

Pour plus d’informations, consultez le thème "ValidationRule Property" dans DAO Help.

## <a name="cdaotabledefgetvalidationtext"></a><a name="getvalidationtext"></a>CDaoTableDef::GetValidationText

Appelez cette fonction pour récupérer la chaîne pour afficher lorsqu’un utilisateur sais voit des données qui ne correspondent pas à la règle de validation.

```
CString GetValidationText();
```

### <a name="return-value"></a>Valeur de retour

Un `CString` objet qui spécifie le texte affiché si l’utilisateur sais voit des données qui ne correspondent pas à la règle de validation.

### <a name="remarks"></a>Notes

Pour `CDaoTableDef` un objet, il s’agit `CString` d’une lecture uniquement pour une table jointe et de lecture/écriture pour une table de base.

Pour plus d’informations connexes, consultez le thème "ValidationText Property" dans DAO Help.

## <a name="cdaotabledefisopen"></a><a name="isopen"></a>CDaoTableDef::IsOpen

Appelez cette fonction de `CDaoTableDef` membre pour déterminer si l’objet est actuellement ouvert.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Valeur de retour

Nonzero si `CDaoTableDef` l’objet est ouvert; sinon 0.

### <a name="remarks"></a>Notes

## <a name="cdaotabledefm_pdatabase"></a><a name="m_pdatabase"></a>CDaoTableDef::m_pDatabase

Contient un pointeur à l’objet [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) pour cette table.

### <a name="remarks"></a>Notes

## <a name="cdaotabledefm_pdaotabledef"></a><a name="m_pdaotabledef"></a>CDaoTableDef::m_pDAOTableDef

Contient un pointeur à l’interface OLE pour `CDaoTableDef` l’objet de dépôt DAO sous-jacent à l’objet.

### <a name="remarks"></a>Notes

Utilisez ce pointeur si vous avez besoin d’accéder à l’interface DAO directement.

## <a name="cdaotabledefopen"></a><a name="open"></a>CDaoTableDef::Ouvert

Appelez cette fonction de membre pour ouvrir un tableau précédemment enregistré dans la collection de tableDef de la base de données.

```
virtual void Open(LPCTSTR lpszName);
```

### <a name="parameters"></a>Paramètres

*lpszName (en)*<br/>
Un pointeur à une chaîne qui spécifie un nom de table.

### <a name="remarks"></a>Notes

## <a name="cdaotabledefrefreshlink"></a><a name="refreshlink"></a>CDaoTableDef::RefreshLink

Appelez cette fonction de membre pour mettre à jour les informations de connexion pour une table jointe.

```cpp
void RefreshLink();
```

### <a name="remarks"></a>Notes

Vous modifiez les informations de connexion pour une `CDaoTableDef` table jointe `RefreshLink` en appelant [SetConnect](#setconnect) sur l’objet correspondant, puis en utilisant la fonction membre pour mettre à jour les informations. Lorsque vous `RefreshLink`appelez, les propriétés de la table ci-jointe ne sont pas modifiées.

Pour forcer l’entrée en vigueur des informations de connexion modifiées, tous les objets [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) ouverts basés sur ce système de dépôt doivent être fermés.

Pour obtenir des informations connexes, consultez le thème « Méthode RefreshLink » dans DAO Help.

## <a name="cdaotabledefsetattributes"></a><a name="setattributes"></a>CDaoTableDef::SetAttributes

Définit une valeur qui indique une `CDaoTableDef` ou plusieurs caractéristiques d’un objet.

```cpp
void SetAttributes(long lAttributes);
```

### <a name="parameters"></a>Paramètres

*lAttributes*<br/>
Caractéristiques du tableau représentés par l’objet `CDaoTableDef` et peuvent être une somme de ces constantes:

|Constant|Description|
|--------------|-----------------|
|`dbAttachExclusive`|Pour les bases de données qui utilisent le moteur de base de données Microsoft Jet, indique que la table est une table attachée ouverte pour une utilisation exclusive.|
|`dbAttachSavePWD`|Pour les bases de données qui utilisent le moteur de base de données Microsoft Jet, indique que l’identifiant utilisateur et le mot de passe pour la table ci-jointe sont enregistrés avec les informations de connexion.|
|`dbSystemObject`|Indique que la table est une table système fournie par le moteur de base de données Microsoft Jet.|
|`dbHiddenObject`|Indique que la table est une table cachée fournie par le moteur de base de données Microsoft Jet.|

### <a name="remarks"></a>Notes

Lors de la définition de plusieurs attributs, vous pouvez les combiner en résumant les constantes appropriées à l’aide de l’opérateur bitwise-OR. Le `dbAttachExclusive` réglage sur une table non attachée produit une exception. La combinaison des valeurs suivantes produit également une exception :

- **dbAttachExclusive &#124; dbAttachedODBC**

- **dbAttachSavePWD &#124; dbAttachedTable**

Pour obtenir des renseignements connexes, consultez le thème « Propriété d’attributs » dans DAO Help.

## <a name="cdaotabledefsetconnect"></a><a name="setconnect"></a>CDaoTableDef::SetConnect

Pour `CDaoTableDef` un objet qui représente une table attachée, l’objet de chaîne se compose d’une ou deux parties (un spécificateur de type base de données et un chemin vers la base de données).

```cpp
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>Paramètres

*lpszConnect*<br/>
Un pointeur à une expression de chaîne qui spécifie des paramètres supplémentaires à passer à ODBC ou les pilotes ISAM installables.

### <a name="remarks"></a>Notes

Le chemin indiqué dans le tableau ci-dessous est le chemin complet pour l’annuaire contenant les fichiers de base de données et doit être précédé par l’identifiant "DATABASE". Dans certains cas (comme avec les bases de données Microsoft Jet et Microsoft Excel), un nom de fichier spécifique est inclus dans l’argument de la trajectoire de base de données.

> [!NOTE]
> N’incluez pas l’espace blanc autour du signe égal\\dans les déclarations de chemin de la forme "DATABASE’drive: 'path'. Cela se traduira par une exception étant jeté et la connexion défaillante.

Le tableau suivant montre les types de bases de données possibles et leurs spécifications et chemins de base de données correspondants :

|Type de base de données|Spécificateur|Path|
|-------------------|---------------|----------|
|Base de données à l’aide du moteur de base de données Jet|"[ `database`];"|" `drive`\\\ :*nom*\\\ *de fichier path*. MDB"|
|dBASE III|"dBASE III;"|" `drive`\\\ :*chemin*"|
|dBASE IV|"dBASE IV;"|" `drive`\\\ :*chemin*"|
|dBASE 5|"dBASE 5.0;"|" `drive`\\\ :*chemin*"|
|Paradoxe 3.x|"Paradoxe 3.x;"|" `drive`\\\ :*chemin*"|
|Paradoxe 4.x|"Paradoxe 4.x;"|" `drive`\\\ :*chemin*"|
|Paradoxe 5.x|"Paradoxe 5.x;"|" `drive`\\\ :*chemin*"|
|Excel 3.0|"Excel 3.0;"|" `drive`\\\ :*nom*\\\ *de fichier path*. XLS"|
|Excel 4.0|"Excel 4.0;"|" `drive`\\\ :*nom*\\\ *de fichier path*. XLS"|
|Excel 5.0 ou Excel 95|"Excel 5.0;"|" `drive`\\\ :*nom*\\\ *de fichier path*. XLS"|
|Excel 97 Annonces|"Excel 8.0;"|" `drive`\\\ :*nom*\ *de fichier path*. XLS"|
|IMPORTATION HTML|"IMPORTATION HTML;"|" `drive`\\\ : nom*de fichier de**chemin*\ "|
|Exportation HTML|"EXPORTATION HTML;"|" `drive`\\\ :*chemin*"|
|Texte|"Texte;"|"drive:\\'chemin"|
|ODBC|"ODBC; BASE `database`DE DONNÉESMD ; Utilisateur *UIDMD*; *Mot de passe*PWDMD ; nom de *source de données DSNMD;* LOGINTIMEOUT *SECONDES;*" (Ce n’est peut-être pas une chaîne de connexion complète pour tous les serveurs; c’est juste un exemple. Il est très important de ne pas avoir d’espaces entre les paramètres.)|None|
|Exchange|"Échange;<br /><br /> DOSSIER MAPILEVELMD *folderpath*;<br /><br /> [TABLETYPEMD 0 &#124; 1 ;]<br /><br /> [PROFIL *PROFILMD profil*;]<br /><br /> [mot *de passe*PWDMD ;]<br /><br /> [BASE `database`DE DONNÉES;]"|*"drive*\\\ :*nom*\\\ *de fichier path*. MDB"|

> [!NOTE]
> Btrieve n’est plus pris en charge à partir de DAO 3.5.

Vous devez utiliser un double\\\\backslash ( ) dans les chaînes de connexion. Si vous avez modifié les propriétés d’une connexion existante à l’aide, `SetConnect`vous devez ensuite appeler [RefreshLink](#refreshlink). Si vous initialisez les `SetConnect`propriétés de `RefreshLink`connexion en utilisant, vous n’avez pas besoin d’appeler, mais si vous choisissez de le faire, d’abord appendice le dépôt.

Si un mot de passe est requis mais non fourni, le conducteur de l’ODBC affiche une boîte de dialogue de connexion la première fois qu’une table est consultée et à nouveau si la connexion est fermée et rouverte.

Vous pouvez définir la `CDaoTableDef` chaîne de connexion d’un objet en fournissant un argument source à la `Create` fonction membre. Vous pouvez vérifier le paramètre pour déterminer le type, le chemin, l’identifiant utilisateur, le mot de passe ou la source de données ODBC de la base de données. Pour plus d’informations, consultez la documentation pour le conducteur spécifique.

Pour obtenir des informations connexes, consultez le thème « Connect Property » dans DAO Help.

## <a name="cdaotabledefsetname"></a><a name="setname"></a>CDaoTableDef::SetName

Appelez cette fonction de membre pour définir un nom défini par l’utilisateur pour une table.

```cpp
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>Paramètres

*lpszName (en)*<br/>
Un pointeur à une expression de chaîne qui spécifie un nom pour une table.

### <a name="remarks"></a>Notes

Le nom doit commencer par une lettre et peut contenir un maximum de 64 caractères. Il peut inclure des nombres et des personnages de souligner, mais ne peut pas inclure la ponctuation ou des espaces.

Pour obtenir des informations connexes, consultez le thème « Propriété du nom » dans DAO Help.

## <a name="cdaotabledefsetsourcetablename"></a><a name="setsourcetablename"></a>CDaoTableDef::SetSourceTableName

Appelez cette fonction de membre pour spécifier le nom d’une table jointe ou le nom du tableau de base sur lequel l’objet `CDaoTableDef` est basé, car il existe dans la source originale des données.

```cpp
void SetSourceTableName(LPCTSTR lpszSrcTableName);
```

### <a name="parameters"></a>Paramètres

*lpszSrcTableName*<br/>
Un pointeur à une expression de chaîne qui spécifie un nom de table dans la base de données externe. Pour une table de base, le réglage est une ficelle vide ("").

### <a name="remarks"></a>Notes

Vous devez alors appeler [RefreshLink](#refreshlink). Ce paramètre de propriété est vide pour une table de base et lu/écrire pour une table jointe ou un objet non joint à une collection.

Pour plus d’informations connexes, consultez le thème "SourceTableName Property" dans DAO Help.

## <a name="cdaotabledefsetvalidationrule"></a><a name="setvalidationrule"></a>CDaoTableDef::SetValidationRule

Appelez cette fonction de membre pour définir une règle de validation pour un dépôt.

```cpp
void SetValidationRule(LPCTSTR lpszValidationRule);
```

### <a name="parameters"></a>Paramètres

*lpszValidationRule*<br/>
Un pointeur à une expression de chaîne qui valide une opération.

### <a name="remarks"></a>Notes

Les règles de validation sont utilisées dans le cadre des opérations de mise à jour. Si un dépôt contient une règle de validation, les mises à jour de ce formulaire doivent correspondre aux critères prédéterminés avant que les données ne soient modifiées. Si la modification ne correspond pas aux critères, une exception contenant le texte de [GetValidationText](#getvalidationtext) s’affiche.

La validation n’est prise en charge que pour les bases de données qui utilisent le moteur de base de données Microsoft Jet. L’expression ne peut pas se référer à des fonctions définies par l’utilisateur, des fonctions agrégées de domaine, des fonctions agrégées SQL ou des requêtes. Une règle de `CDaoTableDef` validation pour un objet peut se référer à plusieurs champs dans cet objet.

Par exemple, pour les domaines *nommés hire_date* et *termination_date*, une règle de validation pourrait être :

[!code-cpp[NVC_MFCDatabase#34](../../mfc/codesnippet/cpp/cdaotabledef-class_1.cpp)]

Pour plus d’informations, consultez le thème "ValidationRule Property" dans DAO Help.

## <a name="cdaotabledefsetvalidationtext"></a><a name="setvalidationtext"></a>CDaoTableDef::SetValidationText

Appelez cette fonction de membre pour définir le `CDaoTableDef` texte d’exception d’une règle de validation pour un objet avec une table de base sous-jacente supportée par le moteur de base Microsoft Jet.

```cpp
void SetValidationText(LPCTSTR lpszValidationText);
```

### <a name="parameters"></a>Paramètres

*lpszValidationText*<br/>
Un pointeur à une expression de chaîne qui spécifie le texte affiché si les données saisies est invalide.

### <a name="remarks"></a>Notes

Vous ne pouvez pas définir le texte de validation d’une table jointe.

Pour plus d’informations connexes, consultez le thème "ValidationText Property" dans DAO Help.

## <a name="see-also"></a>Voir aussi

[Classe CObject](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)<br/>
[CDaoDatabase, classe](../../mfc/reference/cdaodatabase-class.md)<br/>
[Classe CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)
