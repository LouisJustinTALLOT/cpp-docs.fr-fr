---
description: 'En savoir plus sur : TN045 : prise en charge MFC/de base de données pour long varchar/varbinary'
title: 'TN045 : prise en charge MFC-Database pour les Varchar-Varbinary longs'
ms.date: 11/04/2016
helpviewer_keywords:
- TN045
- Varbinary data type
- Varchar data type
ms.assetid: cf572c35-5275-45b5-83df-5f0e36114f40
ms.openlocfilehash: 4e19147ab5ca392307f331b12d3cf24eb5fcc06f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215181"
---
# <a name="tn045-mfcdatabase-support-for-long-varcharvarbinary"></a>TN045 : prise en charge MFC/Database de longs varchar/varbinary

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Cette note décrit comment récupérer et envoyer les **SQL_LONGVARCHAR** ODBC et les types de données **SQL_LONGVARBINARY** à l’aide des classes de base de données MFC.

## <a name="overview-of-long-varcharvarbinary-support"></a>Vue d'ensemble de la prise en charge de Long Varchar/Varbinary

Les types de données ODBC **SQL_LONG_VARCHAR** et **SQL_LONGBINARY** (désignés ici comme colonnes de données longues) peuvent contenir des quantités énormes de données. Vous pouvez gérer ces données de 3 façons :

- Liez-le à un `CString` / `CByteArray` .

- Liez-les à `CLongBinary`.

- Ne les liez pas du tout et récupérez et envoyez la valeur des données de type long manuellement, indépendamment des classes de base de données.

Chacune des trois méthodes présente des avantages et des inconvénients.

Les colonnes de données de type long ne sont pas prises en charge pour les paramètres d'une requête. Elles le sont uniquement pour outputColumns.

## <a name="binding-a-long-data-column-to-a-cstringcbytearray"></a>Liaison d'une colonne de données de type long à CString et CByteArray

Avantages :

Cette approche est simple à comprendre, et vous utilisez des classes qui vous sont familières. Le framework fournit la prise en charge de `CFormView` pour `CString` avec `DDX_Text`. Les classes `CString` et `CByteArray` fournissent un grand nombre de fonctionnalités de chaîne ou de collection générales, et vous pouvez contrôler la quantité de mémoire allouée localement pour contenir la valeur des données. L’infrastructure gère une ancienne copie de données de champ `Edit` pendant `AddNew` les appels de fonction ou, et l’infrastructure peut détecter automatiquement les modifications apportées aux données.

> [!NOTE]
> Étant donné que `CString` est conçu pour travailler sur des données de type caractère et `CByteArray` pour travailler sur des données binaires, il est recommandé de placer les données de caractères (**SQL_LONGVARCHAR**) dans `CString` et les données binaires (**SQL_LONGVARBINARY**) dans `CByteArray` .

Les fonctions RFX pour `CString` et `CByteArray` ont un argument supplémentaire qui vous permet de remplacer la taille par défaut de la mémoire allouée pour contenir la valeur récupérée de la colonne de données. Notez l'argument nMaxLength dans les déclarations de fonction suivantes :

```cpp
void AFXAPI RFX_Text(CFieldExchange* pFX,
    const char *szName,
    CString& value,
    int nMaxLength = 255,
    int nColumnType =
    SQL_VARCHAR);

void AFXAPI RFX_Binary(CFieldExchange* pFX,
    const char *szName,
    CByteArray& value,
    int nMaxLength = 255);
```

Si vous récupérez une colonne de données de type long dans `CString` ou `CByteArray`, la quantité maximale de données retournées est, par défaut, 255 octets. Au-delà, rien ne sera pris en compte. Dans ce cas, l’infrastructure lèvera l’exception **AFX_SQL_ERROR_DATA_TRUNCATED**. Heureusement, vous pouvez augmenter explicitement nMaxLength à des valeurs supérieures, jusqu’à **maxint**.

> [!NOTE]
> La valeur de nMaxLength est utilisée par MFC pour définir la mémoire tampon locale de la `SQLBindColumn` fonction. Il s'agit de la mémoire tampon locale pour le stockage des données, qui n'affecte pas réellement la quantité de données retournées par le pilote ODBC. `RFX_Text` et `RFX_Binary` n’effectuent qu’un seul appel à l’aide `SQLFetch` de pour récupérer les données de la base de données principale. Chaque pilote ODBC a une propre limite sur la quantité de données qu’il peut retourner en une seule récupération. Cette limite peut être nettement inférieure à la valeur définie dans nMaxLength, auquel cas l’exception **AFX_SQL_ERROR_DATA_TRUNCATED** sera levée. Dans ces circonstances, utilisez `RFX_LongBinary` au lieu de `RFX_Text` ou `RFX_Binary` afin que toutes les données puissent être récupérées.

ClassWizard lie un **SQL_LONGVARCHAR** à un `CString` , ou un **SQL_LONGVARBINARY** à un `CByteArray` pour vous. Si vous souhaitez allouer plus de 255 octets dans lesquels vous récupérez la colonne de données de type long, vous pouvez fournir une valeur explicite pour nMaxLength.

Lorsqu’une colonne de données de type long est liée à `CString` ou `CByteArray` , la mise à jour du champ fonctionne de la même façon que lorsqu’il est lié à un SQL_ **varchar** ou SQL_ **varbinary**. Pendant `Edit` , la valeur des données est mise en cache et ultérieurement comparée lorsque `Update` est appelé pour détecter les modifications apportées à la valeur de données et définir correctement les valeurs modifiées et null pour la colonne.

## <a name="binding-a-long-data-column-to-a-clongbinary"></a>Liaison d’une colonne de données de type long à CLongBinary

Si votre colonne de données de type long peut contenir plus de **maxint** d’octets de données, vous devez probablement envisager de la récupérer dans un `CLongBinary` .

Avantages :

Vous récupérez une colonne de données entière de type long, en fonction de la mémoire disponible.

Inconvénients :

Les données sont conservées en mémoire. Cette approche est également extrêmement coûteuse pour de très grandes quantités de données. Vous devez appeler `SetFieldDirty` pour le membre de données lié pour vous assurer que le champ est inclus dans une `Update` opération.

Si vous récupérez des colonnes de données de type long dans `CLongBinary`, les classes de base de données vérifient leur taille totale, puis allouent un segment de mémoire `HGLOBAL` assez grand pour contenir la valeur de données entière. Les classes de base de données récupèrent ensuite la valeur de données entière dans la mémoire allouée `HGLOBAL`.

Si la source de données ne peut pas retourner la taille attendue de la colonne de données de type long, l’infrastructure lèvera l’exception **AFX_SQL_ERROR_SQL_NO_TOTAL**. Si la tentative d'allocation de la mémoire `HGLOBAL` échoue, une exception de mémoire standard est levée.

ClassWizard lie un **SQL_LONGVARCHAR** ou **SQL_LONGVARBINARY** à un `CLongBinary` pour vous. Sélectionnez `CLongBinary` comme type de variable dans la boîte de dialogue Ajouter une variable membre. ClassWizard ajoute ensuite un appel `RFX_LongBinary` à votre appel `DoFieldExchange` et incrémente le nombre total de champs liés.

Pour mettre à jour les valeurs de colonne de données de type long, vérifiez d’abord que le alloué `HGLOBAL` est suffisamment grand pour contenir vos nouvelles données en appelant **:: GlobalSize** sur le membre *m_hData* du `CLongBinary` . Si elle est trop petite, libérez `HGLOBAL` et allouez une mémoire de la taille appropriée. Ensuite, définissez *m_dwDataLength* pour refléter la nouvelle taille.

Dans le cas contraire, si *m_dwDataLength* est supérieure à la taille des données que vous remplacez, vous pouvez libérer et réallouer le `HGLOBAL` ou le conserver alloué. Veillez à indiquer le nombre d’octets réellement utilisés dans *m_dwDataLength*.

## <a name="how-updating-a-clongbinary-works"></a>Fonctionnement de la mise à jour de CLongBinary

Il n'est pas nécessaire de comprendre le fonctionnement de la mise à jour de `CLongBinary`, mais cela peut être utile pour savoir comment envoyer des valeurs de données de type long à une source de données, si vous choisissez cette troisième méthode, décrite ci-dessous.

> [!NOTE]
> Pour qu'un champ `CLongBinary` soit inclus dans une mise à jour, vous devez appeler explicitement `SetFieldDirty` pour ce champ. Si vous apportez des modifications à un champ, notamment en lui affectant la valeur Null, vous devez appeler `SetFieldDirty`. Vous devez également appeler `SetFieldNull` , avec le deuxième paramètre ayant la valeur **false**, pour marquer le champ comme ayant une valeur.

Lors de la mise à jour d’un `CLongBinary` champ, les classes de base de données utilisent le mécanisme d' **DATA_AT_EXEC** d’ODBC (voir la documentation ODBC sur `SQLSetPos` l’argument rgbValue de). Lorsque l’infrastructure prépare l’instruction INSERT ou Update, au lieu de pointer sur le `HGLOBAL` contenant les données, l' *adresse* du `CLongBinary` est définie en tant que *valeur* de la colonne à la place et l’indicateur de longueur est défini sur **SQL_DATA_AT_EXEC**. Plus tard, lorsque l’instruction Update sera envoyée à la source de données, `SQLExecDirect` retournera **SQL_NEED_DATA**. Cela indique à le framework que la valeur du paramètre pour cette colonne est en réalité l'adresse de `CLongBinary`. Le Framework appelle `SQLGetData` une seule fois avec une petite mémoire tampon, en attendant que le pilote retourne la longueur réelle des données. Si le pilote retourne la longueur réelle de l'objet BLOB, MFC réaffecte autant d'espace que nécessaire pour extraire l'objet BLOB. Si la source de données retourne **SQL_NO_TOTAL**, indiquant qu’elle ne peut pas déterminer la taille de l’objet BLOB, MFC créera des blocs plus petits. La taille initiale par défaut est 64 Ko, et les blocs suivants auront une taille deux fois plus grande ; par exemple, le deuxième aura une taille de 128 Ko, le troisième une taille de 256 Ko, et ainsi de suite. La taille initiale est configurable.

## <a name="not-binding-retrievingsending-data-directly-from-odbc-with-sqlgetdata"></a>Absence de liaison : récupération et envoi des données directement depuis ODBC avec SQLGetData

Avec cette méthode, vous ignorez complètement les classes de base de données et gérez vous-même la colonne de données de type long.

Avantages :

Vous pouvez mettre en cache les données sur le disque si nécessaire, ou décider dynamiquement de la quantité de données à récupérer.

Inconvénients :

Vous n’avez pas accès au Framework `Edit` ni `AddNew` à la prise en charge, et vous devez écrire le code vous-même pour effectuer les fonctionnalités de base ( `Delete` ne fonctionne pas, car il ne s’agit pas d’une opération au niveau des colonnes).

Dans ce cas, la colonne de données de type long doit figurer dans la liste de sélection de l'ensemble d'enregistrements, mais le framework ne doit pas la lier. Pour ce faire, vous pouvez fournir votre propre instruction SQL via `GetDefaultSQL` ou en tant qu’argument lpszSQL à `CRecordset` la `Open` fonction de, et ne pas lier la colonne supplémentaire avec un RFX_ appel de fonction. ODBC requiert que les champs indépendants s'affichent à droite des champs liés. En conséquence, ajoutez la ou les colonnes indépendantes à la fin de la liste de sélection.

> [!NOTE]
> Étant donné que la colonne de données de type long n'est pas liée par le framework, les modifications qui y sont apportées ne sont pas gérées avec des appels `CRecordset::Update`. Vous devez créer et envoyer vous-même les instructions SQL **Insert** et **Update** requises.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
