---
title: 'TN045 : Prise en charge de MFC / Database de longs Varchar / Varbinary'
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.data
helpviewer_keywords:
- TN045
- Varbinary data type
- Varchar data type
ms.assetid: cf572c35-5275-45b5-83df-5f0e36114f40
ms.openlocfilehash: d356f094759775f709838de149769b1671fdf9ba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62305370"
---
# <a name="tn045-mfcdatabase-support-for-long-varcharvarbinary"></a>TN045 : Prise en charge MFC/Database de longs Varchar/Varbinary

> [!NOTE]
>  La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Cette note décrit comment récupérer et envoyer ODBC **SQL_LONGVARCHAR** et **SQL_LONGVARBINARY** classes de base de données des types de données à l’aide de la bibliothèque MFC.

## <a name="overview-of-long-varcharvarbinary-support"></a>Vue d'ensemble de la prise en charge de Long Varchar/Varbinary

ODBC **SQL_LONG_VARCHAR** et **SQL_LONGBINARY** (désignées ici comme la durée pendant laquelle les colonnes de données) des types de données peuvent contenir de grandes quantités de données. Vous pouvez gérer ces données de 3 façons :

- Lier à un `CString` / `CByteArray`.

- Liez-les à `CLongBinary`.

- Ne les liez pas du tout et récupérez et envoyez la valeur des données de type long manuellement, indépendamment des classes de base de données.

Chacune des trois méthodes présente des avantages et des inconvénients.

Les colonnes de données de type long ne sont pas prises en charge pour les paramètres d'une requête. Elles le sont uniquement pour outputColumns.

## <a name="binding-a-long-data-column-to-a-cstringcbytearray"></a>Liaison d'une colonne de données de type long à CString et CByteArray

Avantages :

Cette approche est simple à comprendre, et vous utilisez des classes qui vous sont familières. Le framework fournit la prise en charge de `CFormView` pour `CString` avec `DDX_Text`. Les classes `CString` et `CByteArray` fournissent un grand nombre de fonctionnalités de chaîne ou de collection générales, et vous pouvez contrôler la quantité de mémoire allouée localement pour contenir la valeur des données. Le framework conserve une ancienne copie de données de champ pendant `Edit` ou `AddNew` appels de fonction et elle peut détecter automatiquement les modifications apportées aux données pour vous.

> [!NOTE]
>  Dans la mesure où `CString` est conçu pour travailler sur les données de type caractère, et `CByteArray` pour travailler sur des données binaires, il est recommandé de placer les données de caractères (**SQL_LONGVARCHAR**) dans `CString`et les données binaires ( **SQL_LONGVARBINARY**) dans `CByteArray`.

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

Si vous récupérez une colonne de données de type long dans `CString` ou `CByteArray`, la quantité maximale de données retournées est, par défaut, 255 octets. Au-delà, rien ne sera pris en compte. Dans ce cas, le framework lèvera l’exception **AFX_SQL_ERROR_DATA_TRUNCATED**. Heureusement, vous pouvez explicitement augmenter nMaxLength à des valeurs supérieures, jusqu'à **MAXINT**.

> [!NOTE]
>  La valeur de nMaxLength est utilisée par MFC pour définir la mémoire tampon locale de le `SQLBindColumn` (fonction). Il s'agit de la mémoire tampon locale pour le stockage des données, qui n'affecte pas réellement la quantité de données retournées par le pilote ODBC. `RFX_Text` et `RFX_Binary` uniquement appeler une à l’aide de `SQLFetch` pour récupérer les données à partir de la base de données back-end. Chaque pilote ODBC a une propre limite sur la quantité de données qu’il peut retourner en une seule récupération. Cette limite peut être beaucoup plus petite que la valeur définie dans nMaxLength, auquel cas l’exception **AFX_SQL_ERROR_DATA_TRUNCATED** sera levée. Dans ces circonstances, utilisez `RFX_LongBinary` au lieu de `RFX_Text` ou `RFX_Binary` afin que toutes les données puissent être récupérées.

ClassWizard lie un **SQL_LONGVARCHAR** à un `CString`, ou un **SQL_LONGVARBINARY** à un `CByteArray` pour vous. Si vous souhaitez allouer plus de 255 octets dans lesquels vous récupérez la colonne de données de type long, vous pouvez fournir une valeur explicite pour nMaxLength.

Lorsqu’une colonne de données de type long est liée à un `CString` ou `CByteArray`, la mise à jour le champ fonctionne de la même que lorsqu’elle est liée à SQL_**VARCHAR** ou SQL_**VARBINARY**. Au cours de `Edit`, la valeur de données est mis en cache et comparée ultérieurement lorsque `Update` est appelée pour détecter les modifications de données valeur et définir le Dirty et valeurs Null pour la colonne de manière appropriée.

## <a name="binding-a-long-data-column-to-a-clongbinary"></a>Liaison d’une colonne de données de type long à CLongBinary

Si votre colonne de données de type long peut contenir plusieurs **MAXINT** octets de données, vous devez probablement envisager de récupérer dans un `CLongBinary`.

Avantages :

Vous récupérez une colonne de données entière de type long, en fonction de la mémoire disponible.

Inconvénients :

Les données sont conservées en mémoire. Cette approche est également extrêmement coûteuse pour de très grandes quantités de données. Vous devez appeler `SetFieldDirty` pour les données liées membre pour vérifier que le champ est inclus dans un `Update` opération.

Si vous récupérez des colonnes de données de type long dans `CLongBinary`, les classes de base de données vérifient leur taille totale, puis allouent un segment de mémoire `HGLOBAL` assez grand pour contenir la valeur de données entière. Les classes de base de données récupèrent ensuite la valeur de données entière dans la mémoire allouée `HGLOBAL`.

Si la source de données ne peut pas retourner la taille attendue de la colonne de données de type long, le framework lèvera l’exception **AFX_SQL_ERROR_SQL_NO_TOTAL**. Si la tentative d'allocation de la mémoire `HGLOBAL` échoue, une exception de mémoire standard est levée.

ClassWizard lie un **SQL_LONGVARCHAR** ou **SQL_LONGVARBINARY** à un `CLongBinary` pour vous. Sélectionnez `CLongBinary` comme type de variable dans la boîte de dialogue Ajouter une variable membre. ClassWizard ajoute ensuite un appel `RFX_LongBinary` à votre appel `DoFieldExchange` et incrémente le nombre total de champs liés.

Pour mettre à jour de la durée pendant laquelle les valeurs de colonne de données, commencez par vérifier que la mémoire allouée `HGLOBAL` est assez grand pour contenir les nouvelles données en appelant **:: GlobalSize** sur le *m_hData* membre de la `CLongBinary`. Si elle est trop petite, libérez `HGLOBAL` et allouez une mémoire de la taille appropriée. Définissez ensuite *m_dwDataLength* afin de refléter la nouvelle taille.

Sinon, si *m_dwDataLength* est supérieure à la taille des données que vous remplacez, vous pouvez libérer et réallouer les `HGLOBAL`, ou la laisser allouée. Veillez à indiquer le nombre d’octets réellement utilisés dans *m_dwDataLength*.

## <a name="how-updating-a-clongbinary-works"></a>Fonctionnement de la mise à jour de CLongBinary

Il n'est pas nécessaire de comprendre le fonctionnement de la mise à jour de `CLongBinary`, mais cela peut être utile pour savoir comment envoyer des valeurs de données de type long à une source de données, si vous choisissez cette troisième méthode, décrite ci-dessous.

> [!NOTE]
>  Pour qu'un champ `CLongBinary` soit inclus dans une mise à jour, vous devez appeler explicitement `SetFieldDirty` pour ce champ. Si vous apportez des modifications à un champ, notamment en lui affectant la valeur Null, vous devez appeler `SetFieldDirty`. Vous devez également appeler `SetFieldNull`, avec le deuxième paramètre défini **FALSE**, pour marquer le champ comme ayant une valeur.

Lors de la mise à jour un `CLongBinary` champ, les classes de base de données utilisent ODBC **DATA_AT_EXEC** mécanisme (voir la documentation ODBC `SQLSetPos`de l’argument rgbValue). Lorsque le framework prépare l’instruction insert ou update, au lieu de pointer vers le `HGLOBAL` contenant les données, le *adresse* de la `CLongBinary` est défini comme le *valeur* de la colonne au lieu de cela et l’indicateur de longueur définie sur **SQL_DATA_AT_EXEC**. Ensuite, lorsque l’instruction de mise à jour est envoyée à la source de données, `SQLExecDirect` retournera **SQL_NEED_DATA**. Cela indique à le framework que la valeur du paramètre pour cette colonne est en réalité l'adresse de `CLongBinary`. Le framework appelle `SQLGetData` qu’une seule fois, avec une petite mémoire tampon, attendant que le pilote pour retourner la longueur réelle des données. Si le pilote retourne la longueur réelle de l'objet BLOB, MFC réaffecte autant d'espace que nécessaire pour extraire l'objet BLOB. Si la source de données retourne **SQL_NO_TOTAL**, indiquant qu’il ne peut pas déterminer la taille de l’objet BLOB, MFC crée des blocs plus petits. La taille initiale par défaut est 64 Ko, et les blocs suivants auront une taille deux fois plus grande ; par exemple, le deuxième aura une taille de 128 Ko, le troisième une taille de 256 Ko, et ainsi de suite. La taille initiale est configurable.

## <a name="not-binding-retrievingsending-data-directly-from-odbc-with-sqlgetdata"></a>Ne pas de liaison : Récupération et envoi des données directement à partir d’ODBC avec SQLGetData

Avec cette méthode, vous ignorez complètement les classes de base de données et gérez vous-même la colonne de données de type long.

Avantages :

Vous pouvez mettre en cache les données sur le disque si nécessaire, ou décider dynamiquement de la quantité de données à récupérer.

Inconvénients :

Vous n’obtenez pas le framework `Edit` ou `AddNew` prise en charge et vous devez écrire du code vous-même pour exécuter des fonctionnalités de base (`Delete` fonctionne cependant, dans la mesure où il n’est pas une opération au niveau de colonne).

Dans ce cas, la colonne de données de type long doit figurer dans la liste de sélection de l'ensemble d'enregistrements, mais le framework ne doit pas la lier. Une façon de procéder consiste à fournir votre propre instruction SQL via `GetDefaultSQL` ou comme argument lpszSQL de `CRecordset`de `Open` de fonction et pas lier la colonne supplémentaire avec une valeur de la fonction rfx_. ODBC requiert que les champs indépendants s'affichent à droite des champs liés. En conséquence, ajoutez la ou les colonnes indépendantes à la fin de la liste de sélection.

> [!NOTE]
>  Étant donné que la colonne de données de type long n'est pas liée par le framework, les modifications qui y sont apportées ne sont pas gérées avec des appels `CRecordset::Update`. Vous devez créer et envoyer le code SQL requis **insérer** et **mise à jour** instructions vous-même.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
