---
title: 'TN043 : Routines RFX | Microsoft Docs'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- RFX
dev_langs:
- C++
helpviewer_keywords:
- RFX (record field exchange), architecture
- TN043
- RFX (record field exchange)
ms.assetid: f552d0c1-2c83-4389-b472-42c9940aa713
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d1266097f9d548630459a3fb45ed75edb811deea
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44317340"
---
# <a name="tn043-rfx-routines"></a>TN043 : routines RFX

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Cette note décrit l’architecture d’exchange (RFX) de champs d’enregistrements. Elle décrit également la façon dont vous écrivez un **RFX_** procédure.

## <a name="overview-of-record-field-exchange"></a>Vue d’ensemble de Record Field Exchange

Toutes les fonctions de champ de recordset sont effectuées avec le code C++. Il n’existe aucune des ressources spéciales ou des macros magiques. Le cœur du mécanisme est une fonction virtuelle qui doit être substituée dans chaque classe dérivée de jeu d’enregistrements. Il existe toujours dans ce formulaire :

```cpp
void CMySet::DoFieldExchange(CFieldExchange* pFX)
{
    //{{AFX_FIELD_MAP(CMySet)
        <recordset exchange field type call>
        <recordset exchange function call>
    //}}AFX_FIELD_MAP
}
```

Les commentaires AFX format spécial autoriser ClassWizard localiser et modifier le code au sein de cette fonction. Code qui n’est pas compatible avec ClassWizard doit être placé en dehors des commentaires de formats spéciaux.

Dans l’exemple ci-dessus, \<recordset_exchange_field_type_call > se présente sous la forme :

```cpp
pFX->SetFieldType(CFieldExchange::outputColumn);
```

et \<recordset_exchange_function_call > se présente sous la forme :

```cpp
RFX_Custom(pFX, "Col2", m_Col2);
```

La plupart des **RFX_** fonctions ont trois arguments, comme indiqué ci-dessus, mais certains (par exemple, `RFX_Text` et `RFX_Binary`) ont des arguments facultatifs supplémentaires.

Plusieurs **RFX_** peut être inclus dans chaque `DoDataExchange` (fonction).

Consultez « afxdb.h » pour obtenir la liste de toutes les routines d’échange de champ de recordset fournis avec MFC.

Appels de champ de Recordset sont un moyen de l’inscription des emplacements de mémoire (généralement les membres de données) pour stocker les données de champ pour un `CMySet` classe.

## <a name="notes"></a>Notes

Fonctions de champ de Recordset sont conçues pour fonctionner uniquement avec la `CRecordset` classes. Ils ne sont pas généralement utilisables par d’autres classes MFC.

Les valeurs initiales de données sont définies dans le constructeur C++ standard, généralement dans un bloc avec `//{{AFX_FIELD_INIT(CMylSet)` et `//}}AFX_FIELD_INIT` commentaires.

Chaque **RFX_** fonction doit prendre en charge diverses opérations, allant de retour de l’état de non-intégrité du champ à l’archivage du champ de préparation pour la modification du champ.

Chaque fonction qui appelle `DoFieldExchange` (par exemple `SetFieldNull`, `IsFieldDirty`), est son propre initialisation autour de l’appel à `DoFieldExchange`.

## <a name="how-does-it-work"></a>Comment cela fonctionne-t-il

Vous n’avez pas besoin de comprendre ce qui suit afin d’utiliser l’échange de champs d’enregistrements. Toutefois, comprendre comment cela fonctionne en arrière-plan vous aidera à écrire votre propre procédure exchange.

Le `DoFieldExchange` fonction membre est très similaire à la `Serialize` fonction membre, il est responsable de l’obtention ou la définition des données vers/à partir d’un formulaire externe (dans ce cas colonnes à partir du résultat d’une requête ODBC) depuis/vers des données de membre dans la classe. Le *pFX* paramètre est le contexte qui permet d’effectuer l’échange de données et est semblable à la *CArchive* paramètre `CObject::Serialize`. Le *pFX* (un `CFieldExchange` objet) a un indicateur d’opération, ce qui revient à, mais une généralisation de la *CArchive* indicateur de direction. Une fonction RFX peut avoir prendre en charge les opérations suivantes :

- `BindParam` — Indiquer où ODBC doit récupérer les données de paramètre

- `BindFieldToColumn` — Indiquer où ODBC doit récupérer/dépôt outputColumn données

- `Fixup` : Définissez `CString/CByteArray` longueurs, définir le statut de valeur NULL de type bit

- `MarkForAddNew` — Mark incorrectes si la valeur a changé depuis l’appel de AddNew

- `MarkForUpdate` — Mark incorrectes si valeur a changé depuis l’appel de modification

- `Name` Ajouter des noms de champs pour les champs marqués comme modifiés

- `NameValue` — Ajoutez «\<nom de colonne > = » pour les champs marqués comme modifiés

- `Value` — Ajoutez « » suivi d’un séparateur, comme ',' ou ' '

- `SetFieldDirty` : Définition de champ (autrement dit, modifiées) dirty bits d’état

- `SetFieldNull` : Définissez le bit d’état indiquant la valeur null pour le champ

- `IsFieldDirty` : Retourne la valeur du bit de l’état modifié

- `IsFieldNull` : Retourne la valeur du bit de l’état null

- `IsFieldNullable` : Renvoie la valeur TRUE si le champ peut contenir des valeurs NULL

- `StoreField` : Valeur du champ archive

- `LoadField` — Recharger la valeur du champ archivées

- `GetFieldInfoValue` — Retournent des informations générales sur un champ

- `GetFieldInfoOrdinal` — Retournent des informations générales sur un champ

## <a name="user-extensions"></a>Extensions de l’utilisateur

Il existe plusieurs façons d’étendre le mécanisme RFX par défaut. Vous pouvez

- Ajouter de nouveaux types de données. Exemple :

    ```cpp
    CBookmark
    ```

- Ajouter de nouvelles procédures exchange (RFX_).

    ```cpp
    void AFXAPI RFX_Bigint(CFieldExchange* pFX,
        const char *szName,
        BIGINT& value);
    ```

- Avoir le `DoFieldExchange` fonction membre inclure de façon conditionnelle des appels RFX supplémentaires ou toute autre instruction C++ valide.

    ```cpp
    while (posExtraFields != NULL)
    {
        RFX_Text(pFX,
        m_listName.GetNext(posExtraFields),
        m_listValue.GetNext(posExtraValues));
    }
    ```

> [!NOTE]
> Ce code ne peut pas être modifié par ClassWizard et doit être utilisé uniquement en dehors des commentaires de formats spéciaux.

## <a name="writing-a-custom-rfx"></a>Écriture d’un RFX personnalisé

Pour écrire votre propre fonction personnalisée RFX, il est recommandé que vous copiez une fonction RFX existante et modifiez en fonction de vos besoins. En sélectionnant le RFX droit pour copier peut faciliter votre travail. Certaines fonctions RFX ont certaines propriétés uniques que vous devez prendre en compte lorsque vous décidez de laquelle copier.

`RFX_Long` et `RFX_Int`: ce sont les fonctions RFX la plus simple. La valeur de données n’a pas besoin de toute interprétation spéciale, et la taille des données est fixe.

`RFX_Single` et `RFX_Double`: RFX_Long comme RFX_Int ci-dessus, ces fonctions sont simples et faire utiliser largement de l’implémentation par défaut. Ils sont stockés dans dbflt.cpp au lieu de dbrfx.cpp, toutefois, pour activer le chargement du runtime bibliothèque virgule flottante uniquement lorsqu’ils sont explicitement référence.

`RFX_Text` et `RFX_Binary`: ces deux fonctions allouer une mémoire tampon statique pour contenir les informations de type chaîne ou binaire et doit l’inscrire ces mémoires tampons avec ODBC SQLBindCol au lieu de la & valeur de l’inscription. Pour cette raison, ces deux fonctions ont un grand nombre de code spécial.

`RFX_Date`: ODBC retourne les informations de date / heure dans leur propre structure de données TIMESTAMP_STRUCT. Cette fonction alloue dynamiquement un TIMESTAMP_STRUCT comme un « proxy » pour envoyer et recevoir des données de temps de date. Diverses opérations doivent transférer les informations de date et d’heure entre le C++ `CTime` objet et le proxy TIMESTAMP_STRUCT. Cela complique considérablement la cette fonction, mais c’est un bon exemple montrant comment utiliser un proxy pour le transfert de données.

`RFX_LongBinary`: Il s’agit de la bibliothèque de classes seule fonction RFX qui n’utilise pas de liaison de colonne pour recevoir et envoyer des données. Cette fonction ignore l’opération BindFieldToColumn au lieu de cela, lors de l’opération de correction, alloue le stockage pour contenir les données entrantes SQL_LONGVARCHAR ou SQL_LONGVARBINARY, puis effectue un appel de SQLGetData pour récupérer la valeur dans le stockage alloué. Lorsque vous préparez à renvoyer des valeurs de données à la source de données (telles que les opérations NameValue et valeur), cette fonction utilise les fonctionnalités DATA_AT_EXEC d’ODBC. Consultez [Note technique 45](../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md) pour plus d’informations sur l’utilisation des SQL_LONGVARBINARY et SQL_LONGVARCHARs.

Lorsque vous écrivez votre propre **RFX_** (fonction), vous serez souvent être en mesure d’utiliser `CFieldExchange::Default` pour implémenter une opération donnée. Examinez l’implémentation de la valeur par défaut pour l’opération en question. Si elle effectue l’opération vous écririez votre **RFX_** fonction, vous pouvez déléguer à la `CFieldExchange::Default`. Vous pouvez voir des exemples de l’appel `CFieldExchange::Default` dans dbrfx.cpp

Il est important d’appeler `IsFieldType` au début de votre fonction RFX et retournent immédiatement si elle retourne FALSE. Ce mécanisme conserve le paramètre exécuter les opérations de sur *outputColumns*et vice versa (comme appeler `BindParam` sur un *outputColumn*). En outre, `IsFieldType` de données suit automatiquement le nombre de *outputColumns* (*m_nFields*) et params (*m_nParams*).

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)  
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)  
