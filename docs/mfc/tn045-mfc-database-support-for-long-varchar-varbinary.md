---
title: 'TN045: Support MFC-Base de données pour Le Long Varchar-Varbinary'
ms.date: 11/04/2016
helpviewer_keywords:
- TN045
- Varbinary data type
- Varchar data type
ms.assetid: cf572c35-5275-45b5-83df-5f0e36114f40
ms.openlocfilehash: f67d159fb600dcacd8eedd40e672edf18bddee9a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365512"
---
# <a name="tn045-mfcdatabase-support-for-long-varcharvarbinary"></a>TN045 : prise en charge MFC/Database de longs varchar/varbinary

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Cette note décrit comment récupérer et envoyer les types **de données de SQL_LONGVARCHAR** et de SQL_LONGVARBINARY de l’ODBC à l’aide des classes de base de données MFC. **SQL_LONGVARBINARY**

## <a name="overview-of-long-varcharvarbinary-support"></a>Vue d'ensemble de la prise en charge de Long Varchar/Varbinary

Les types **de données ODBC SQL_LONG_VARCHAR** et **SQL_LONGBINARY** (appelés ici comme de longues colonnes de données) peuvent contenir d’énormes quantités de données. Vous pouvez gérer ces données de 3 façons :

- Lier à `CString` / `CByteArray`un .

- Liez-les à `CLongBinary`.

- Ne les liez pas du tout et récupérez et envoyez la valeur des données de type long manuellement, indépendamment des classes de base de données.

Chacune des trois méthodes présente des avantages et des inconvénients.

Les colonnes de données de type long ne sont pas prises en charge pour les paramètres d'une requête. Elles le sont uniquement pour outputColumns.

## <a name="binding-a-long-data-column-to-a-cstringcbytearray"></a>Liaison d'une colonne de données de type long à CString et CByteArray

Avantages :

Cette approche est simple à comprendre, et vous utilisez des classes qui vous sont familières. Le framework fournit la prise en charge de `CFormView` pour `CString` avec `DDX_Text`. Les classes `CString` et `CByteArray` fournissent un grand nombre de fonctionnalités de chaîne ou de collection générales, et vous pouvez contrôler la quantité de mémoire allouée localement pour contenir la valeur des données. Le cadre conserve une vieille copie `Edit` `AddNew` des données sur le terrain pendant ou des appels de fonction, et le cadre peut détecter automatiquement les modifications apportées aux données pour vous.

> [!NOTE]
> Depuis `CString` est conçu pour travailler `CByteArray` sur les données de caractère, et pour travailler sur les `CString`données binaires, il est recommandé que vous mettez les données de caractère (**SQL_LONGVARCHAR**) dans , et les données binaires (**SQL_LONGVARBINARY**) dans `CByteArray`.

Les fonctions RFX pour `CString` et `CByteArray` ont un argument supplémentaire qui vous permet de remplacer la taille par défaut de la mémoire allouée pour contenir la valeur récupérée de la colonne de données. Notez l'argument nMaxLength dans les déclarations de fonction suivantes :

```
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

Si vous récupérez une colonne de données de type long dans `CString` ou `CByteArray`, la quantité maximale de données retournées est, par défaut, 255 octets. Au-delà, rien ne sera pris en compte. Dans ce cas, le cadre jettera l’exception **AFX_SQL_ERROR_DATA_TRUNCATED**. Heureusement, vous pouvez augmenter explicitement nMaxLength à de plus grandes valeurs, jusqu’à **MAXINT**.

> [!NOTE]
> La valeur de nMaxLength est utilisée par MFC `SQLBindColumn` pour définir le tampon local de la fonction. Il s'agit de la mémoire tampon locale pour le stockage des données, qui n'affecte pas réellement la quantité de données retournées par le pilote ODBC. `RFX_Text`et `RFX_Binary` ne faites `SQLFetch` qu’un seul appel à l’aide de récupérer les données de la base de données back-end. Chaque pilote ODBC a une propre limite sur la quantité de données qu’il peut retourner en une seule récupération. Cette limite peut être beaucoup plus faible que la valeur définie dans nMaxLength, auquel cas l’exception **AFX_SQL_ERROR_DATA_TRUNCATED** sera jetée. Dans ces circonstances, utilisez `RFX_LongBinary` au lieu de `RFX_Text` ou `RFX_Binary` afin que toutes les données puissent être récupérées.

ClassWizard liera un **SQL_LONGVARCHAR** à `CString`un, **SQL_LONGVARBINARY** ou un SQL_LONGVARBINARY `CByteArray` à un pour vous. Si vous souhaitez allouer plus de 255 octets dans lesquels vous récupérez la colonne de données de type long, vous pouvez fournir une valeur explicite pour nMaxLength.

Lorsqu’une longue colonne de `CString` `CByteArray`données est liée à un ou, la mise à jour du champ fonctionne exactement comme quand il est lié à un SQL_**VARCHAR** ou SQL_**VARBINARY**. Pendant, `Edit`la valeur des données est `Update` mise en cache et comparée plus tard lorsqu’elle est appelée pour détecter les modifications apportées à la valeur des données et définir les valeurs Sales et Null pour la colonne de manière appropriée.

## <a name="binding-a-long-data-column-to-a-clongbinary"></a>Liaison d’une colonne de données de type long à CLongBinary

Si votre longue colonne de données peut contenir plus d’octets **MAXINT** `CLongBinary`de données, vous devriez probablement envisager de les récupérer dans un .

Avantages :

Vous récupérez une colonne de données entière de type long, en fonction de la mémoire disponible.

Inconvénients :

Les données sont conservées en mémoire. Cette approche est également extrêmement coûteuse pour de très grandes quantités de données. Vous devez `SetFieldDirty` demander au membre des données consolidés `Update` de s’assurer que le champ est inclus dans une opération.

Si vous récupérez des colonnes de données de type long dans `CLongBinary`, les classes de base de données vérifient leur taille totale, puis allouent un segment de mémoire `HGLOBAL` assez grand pour contenir la valeur de données entière. Les classes de base de données récupèrent ensuite la valeur de données entière dans la mémoire allouée `HGLOBAL`.

Si la source de données ne peut pas retourner la taille prévue de la longue colonne de données, le cadre jettera l’exception **AFX_SQL_ERROR_SQL_NO_TOTAL**. Si la tentative d'allocation de la mémoire `HGLOBAL` échoue, une exception de mémoire standard est levée.

ClassWizard liera un **SQL_LONGVARCHAR** ou **SQL_LONGVARBINARY** `CLongBinary` à un pour vous. Sélectionnez `CLongBinary` comme type de variable dans la boîte de dialogue Ajouter une variable membre. ClassWizard ajoute ensuite un appel `RFX_LongBinary` à votre appel `DoFieldExchange` et incrémente le nombre total de champs liés.

Pour mettre à jour les valeurs de `HGLOBAL` colonnes de données longues, assurez-vous d’abord que l’allocation `CLongBinary`est suffisamment grande pour conserver vos nouvelles données en appelant **::GlobalSize** sur le *m_hData* membre de la . Si elle est trop petite, libérez `HGLOBAL` et allouez une mémoire de la taille appropriée. Ensuite, *définissez m_dwDataLength* pour refléter la nouvelle taille.

Sinon, si *m_dwDataLength* est plus grande que la taille des données que vous remplacez, `HGLOBAL`vous pouvez soit libérer et réaffecter le , ou le laisser alloué. Assurez-vous d’indiquer le nombre d’octets réellement utilisés dans *m_dwDataLength*.

## <a name="how-updating-a-clongbinary-works"></a>Fonctionnement de la mise à jour de CLongBinary

Il n'est pas nécessaire de comprendre le fonctionnement de la mise à jour de `CLongBinary`, mais cela peut être utile pour savoir comment envoyer des valeurs de données de type long à une source de données, si vous choisissez cette troisième méthode, décrite ci-dessous.

> [!NOTE]
> Pour qu'un champ `CLongBinary` soit inclus dans une mise à jour, vous devez appeler explicitement `SetFieldDirty` pour ce champ. Si vous apportez des modifications à un champ, notamment en lui affectant la valeur Null, vous devez appeler `SetFieldDirty`. Vous devez `SetFieldNull`également appeler , avec le deuxième paramètre étant **FALSE**, pour marquer le champ comme ayant une valeur.

Lors de `CLongBinary` la mise à jour d’un champ, les classes de base `SQLSetPos`de données utilisent le mécanisme de **DATA_AT_EXEC** d’ODBC (voir la documentation de l’ODBC sur l’argument rgbValue). Lorsque le cadre prépare l’insérer ou `HGLOBAL` l’énoncé de mise `CLongBinary` à jour, au lieu de pointer vers la contenant des données, *l’adresse* de la est définie comme la *valeur* de la colonne à la place, et l’indicateur de longueur réglé pour **SQL_DATA_AT_EXEC**. Plus tard, lorsque l’instruction de `SQLExecDirect` mise à jour est envoyée à la source de données, retournera **SQL_NEED_DATA**. Cela indique à le framework que la valeur du paramètre pour cette colonne est en réalité l'adresse de `CLongBinary`. Le cadre `SQLGetData` appelle une fois avec un petit tampon, s’attendant à ce que le conducteur retourne la longueur réelle des données. Si le pilote retourne la longueur réelle de l'objet BLOB, MFC réaffecte autant d'espace que nécessaire pour extraire l'objet BLOB. Si la source de données revient **SQL_NO_TOTAL**, indiquant qu’elle ne peut pas déterminer la taille du BLOB, MFC créera des blocs plus petits. La taille initiale par défaut est 64 Ko, et les blocs suivants auront une taille deux fois plus grande ; par exemple, le deuxième aura une taille de 128 Ko, le troisième une taille de 256 Ko, et ainsi de suite. La taille initiale est configurable.

## <a name="not-binding-retrievingsending-data-directly-from-odbc-with-sqlgetdata"></a>Absence de liaison : récupération et envoi des données directement depuis ODBC avec SQLGetData

Avec cette méthode, vous ignorez complètement les classes de base de données et gérez vous-même la colonne de données de type long.

Avantages :

Vous pouvez mettre en cache les données sur le disque si nécessaire, ou décider dynamiquement de la quantité de données à récupérer.

Inconvénients :

Vous n’obtenez pas le `Edit` `AddNew` cadre ou le support, et vous devez`Delete` écrire du code vous-même pour effectuer la fonctionnalité de base (fonctionne bien, car il ne s’agit pas d’une opération de niveau colonne).

Dans ce cas, la colonne de données de type long doit figurer dans la liste de sélection de l'ensemble d'enregistrements, mais le framework ne doit pas la lier. Une façon de le faire est de `GetDefaultSQL` fournir votre propre déclaration SQL `CRecordset`via `Open` ou comme l’argument lpszSQL à la fonction de «s, et ne pas lier la colonne supplémentaire avec un appel de fonction RFX_. ODBC requiert que les champs indépendants s'affichent à droite des champs liés. En conséquence, ajoutez la ou les colonnes indépendantes à la fin de la liste de sélection.

> [!NOTE]
> Étant donné que la colonne de données de type long n'est pas liée par le framework, les modifications qui y sont apportées ne sont pas gérées avec des appels `CRecordset::Update`. Vous devez créer et envoyer vous-même les déclarations SQL **INSERT** et **UPDATE** requises.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
