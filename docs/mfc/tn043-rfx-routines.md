---
description: 'En savoir plus sur : TN043 : routines RFX'
title: 'TN043 : routines RFX'
ms.date: 06/28/2018
f1_keywords:
- RFX
helpviewer_keywords:
- RFX (record field exchange), architecture
- TN043
- RFX (record field exchange)
ms.assetid: f552d0c1-2c83-4389-b472-42c9940aa713
ms.openlocfilehash: 6e5ac8271739e5cab80b79cb915b07e7d25622cf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215220"
---
# <a name="tn043-rfx-routines"></a>TN043 : routines RFX

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Cette note décrit l’architecture RFX (Record Field Exchange). Elle explique également comment écrire une procédure **RFX_** .

## <a name="overview-of-record-field-exchange"></a>Vue d’ensemble de l’échange de champs d’enregistrements

Toutes les fonctions de champ du Recordset sont effectuées avec du code C++. Il n’existe aucune ressource spéciale ou macros magiques. Le cœur du mécanisme est une fonction virtuelle qui doit être substituée dans chaque classe de Recordset dérivée. Il se trouve toujours sous la forme suivante :

```cpp
void CMySet::DoFieldExchange(CFieldExchange* pFX)
{
    //{{AFX_FIELD_MAP(CMySet)
        <recordset exchange field type call>
        <recordset exchange function call>
    //}}AFX_FIELD_MAP
}
```

Les commentaires AFX de format spécial permettent à ClassWizard de localiser et de modifier le code dans cette fonction. Le code qui n’est pas compatible avec ClassWizard doit être placé en dehors des commentaires de format spéciaux.

Dans l’exemple ci-dessus, \<recordset_exchange_field_type_call> se présente sous la forme :

```cpp
pFX->SetFieldType(CFieldExchange::outputColumn);
```

et \<recordset_exchange_function_call> se présente sous la forme :

```cpp
RFX_Custom(pFX, "Col2", m_Col2);
```

La plupart des **RFX_** fonctions ont trois arguments comme indiqué ci-dessus, mais certains (par exemple `RFX_Text` et `RFX_Binary` ) comportent des arguments facultatifs supplémentaires.

Plusieurs **RFX_** peuvent être inclus dans chaque `DoDataExchange` fonction.

Consultez « AFXDB. h » pour obtenir la liste de toutes les routines d’échange de champs d’ensemble d’enregistrements fournies avec MFC.

Les appels de champ Recordset sont un moyen d’inscrire des emplacements de mémoire (généralement des données membres) pour stocker les données de champ d’une `CMySet` classe.

## <a name="notes"></a>Remarques

Les fonctions de champ Recordset sont conçues pour fonctionner uniquement avec les `CRecordset` classes. Elles ne sont généralement pas utilisables par d’autres classes MFC.

Les valeurs initiales des données sont définies dans le constructeur C++ standard, généralement dans un bloc avec des `//{{AFX_FIELD_INIT(CMylSet)` `//}}AFX_FIELD_INIT` commentaires et.

Chaque fonction de **RFX_** doit prendre en charge diverses opérations, allant de l’état de modification du champ à l’archivage du champ en préparation pour la modification du champ.

Chaque fonction qui appelle `DoFieldExchange` (par exemple `SetFieldNull` , `IsFieldDirty` ) effectue sa propre initialisation autour de l’appel à `DoFieldExchange` .

## <a name="how-does-it-work"></a>Comment cela fonctionne-t-il ?

Vous n’avez pas besoin de comprendre les éléments suivants pour pouvoir utiliser l’échange de champs d’enregistrement. Toutefois, comprendre comment cela fonctionne en arrière-plan vous aide à écrire votre propre procédure Exchange.

La `DoFieldExchange` fonction membre est semblable à la `Serialize` fonction membre. elle est chargée d’obtenir ou de définir des données vers/à partir d’un formulaire externe (dans ce cas, les colonnes du résultat d’une requête ODBC) à partir de/vers les données de membre de la classe. Le paramètre *pfx* est le contexte de l’échange de données et est semblable au paramètre *CArchive* de `CObject::Serialize` . Le fichier *pfx* (un `CFieldExchange` objet) a un indicateur d’opération, qui est similaire à, mais une généralisation de l’indicateur de direction *CArchive* . Une fonction RFX peut avoir besoin de prendre en charge les opérations suivantes :

- `BindParam` : Indiquez où ODBC doit récupérer les données de paramètre

- `BindFieldToColumn` : Indiquez où ODBC doit récupérer/déposer les données outputColumn

- `Fixup` — Définir `CString/CByteArray` des longueurs, définir le bit d’État null

- `MarkForAddNew` — Marquer Dirty si la valeur a changé depuis l’appel AddNew

- `MarkForUpdate` — Marquer Dirty si la valeur a changé depuis l’appel de modification

- `Name` — Ajouter des noms de champ pour les champs marqués comme modifiés

- `NameValue` — Append " \<column name> =" pour les champs marqués comme modifiés

- `Value` — Ajoutez "" suivi d’un séparateur, par exemple', 'ou' '

- `SetFieldDirty` — Définir le champ bit d’État (modifié)

- `SetFieldNull` — Définir le bit d’état indiquant la valeur null pour le champ

- `IsFieldDirty` — Valeur de retour du bit d’état de modification

- `IsFieldNull` — Valeur de retour du bit d’État null

- `IsFieldNullable` — Retourne la valeur TRUE si le champ peut contenir des valeurs NULL

- `StoreField` : Archive la valeur du champ

- `LoadField` : Recharger la valeur du champ archivé

- `GetFieldInfoValue` — Retourne des informations générales sur un champ

- `GetFieldInfoOrdinal` — Retourne des informations générales sur un champ

## <a name="user-extensions"></a>Extensions utilisateur

Il existe plusieurs façons d’étendre le mécanisme RFX par défaut. Vous pouvez :

- Ajoutez de nouveaux types de données. Par exemple :

    ```cpp
    CBookmark
    ```

- Ajoutez de nouvelles procédures Exchange (RFX_).

    ```cpp
    void AFXAPI RFX_Bigint(CFieldExchange* pFX,
        const char *szName,
        BIGINT& value);
    ```

- Faire en sorte que la `DoFieldExchange` fonction membre inclue des appels RFX supplémentaires ou toute autre instruction C++ valide.

    ```cpp
    while (posExtraFields != NULL)
    {
        RFX_Text(pFX,
        m_listName.GetNext(posExtraFields),
        m_listValue.GetNext(posExtraValues));
    }
    ```

> [!NOTE]
> Ce code ne peut pas être modifié par ClassWizard et doit être utilisé uniquement en dehors des commentaires de format spéciaux.

## <a name="writing-a-custom-rfx"></a>Écriture d’un RFX personnalisé

Pour écrire votre propre fonction RFX personnalisée, il est recommandé de copier une fonction RFX existante et de la modifier à vos propres besoins. Le fait de sélectionner le bon RFX pour copier peut faciliter votre travail. Certaines fonctions RFX possèdent des propriétés uniques que vous devez prendre en compte lorsque vous décidez de la copie.

`RFX_Long` et `RFX_Int` : il s’agit des fonctions RFX les plus simples. La valeur des données n’a pas besoin d’une interprétation spéciale et la taille des données est fixe.

`RFX_Single` et `RFX_Double` : comme RFX_Long et RFX_Int ci-dessus, ces fonctions sont simples et peuvent largement utiliser l’implémentation par défaut. Toutefois, elles sont stockées dans dbflt. cpp au lieu de dbrfx. cpp, pour permettre le chargement de la bibliothèque à virgule flottante du runtime uniquement lorsqu’elles sont explicitement référencées.

`RFX_Text` et `RFX_Binary` : ces deux fonctions préallouent une mémoire tampon statique pour contenir des informations de chaîne/binaire, et doivent inscrire ces mémoires tampons avec ODBC SQLBindCol au lieu d’inscrire &valeur. Pour cette raison, ces deux fonctions possèdent un grand nombre de codes de cas spéciaux.

`RFX_Date`: ODBC retourne les informations de date et d’heure dans leur propre structure de données TIMESTAMP_STRUCT. Cette fonction alloue dynamiquement un TIMESTAMP_STRUCT en tant que « proxy » pour l’envoi et la réception de données de date et d’heure. Diverses opérations doivent transférer les informations de date et d’heure entre l' `CTime` objet C++ et le proxy TIMESTAMP_STRUCT. Cela complique considérablement cette fonction, mais il s’agit d’un bon exemple d’utilisation d’un proxy pour le transfert de données.

`RFX_LongBinary`: Il s’agit de la seule fonction RFX de la bibliothèque de classes qui n’utilise pas de liaison de colonne pour recevoir et envoyer des données. Cette fonction ignore l’opération BindFieldToColumn et, au cours de l’opération de correction, alloue le stockage pour stocker les données SQL_LONGVARCHAR ou SQL_LONGVARBINARY entrantes, puis effectue un appel SQLGetData pour récupérer la valeur dans le stockage alloué. Lorsque vous vous préparez à envoyer des valeurs de données à la source de données (par exemple, les opérations de NameValue et de valeur), cette fonction utilise les fonctionnalités de DATA_AT_EXEC d’ODBC. Consultez la [note technique 45](../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md) pour plus d’informations sur l’utilisation de SQL_LONGVARBINARY et SQL_LONGVARCHARs.

Lors de l’écriture de votre propre fonction **RFX_** , vous serez souvent en mesure d’utiliser `CFieldExchange::Default` pour implémenter une opération donnée. Examinez l’implémentation de par défaut pour l’opération en question. S’il effectue l’opération, vous écrirez dans votre fonction **RFX_** vous pouvez déléguer au `CFieldExchange::Default` . Vous pouvez voir des exemples d’appels `CFieldExchange::Default` dans dbrfx. cpp

Il est important d’appeler `IsFieldType` au début de votre fonction RFX et de retourner immédiatement si elle retourne false. Ce mécanisme empêche l’exécution d’opérations de paramètres sur *outputColumns*, et vice versa (comme `BindParam` l’appel de sur un *outputColumn*). En outre, `IsFieldType` effectue automatiquement le suivi du nombre de *outputColumns* (*m_nFields*) et des paramètres (*m_nParams*).

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
