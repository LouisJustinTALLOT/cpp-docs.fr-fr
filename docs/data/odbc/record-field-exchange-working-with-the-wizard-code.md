---
description: 'En savoir plus sur : Record Field Exchange : utilisation du code de l’Assistant'
title: "Record Field Exchange : utilisation du code écrit par l'Assistant"
ms.date: 05/09/2019
helpviewer_keywords:
- DoFieldExchange method, overriding
- Unicode, with database classes
- field data members, declaring
- RFX (ODBC), wizard code
- RFX (ODBC), implementing
- field data members
- ODBC, RFX
- m_nParams data member, initializing
- m_nFields data member
- m_nParams data member
- overriding, DoFieldExchange
- m_nFields data member, initializing
ms.assetid: f00d882a-ff1b-4a75-9717-98d8762bb237
ms.openlocfilehash: c6b44c7c5e3ec09e02e70ad5dd0fecfa434cc0a0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97278712"
---
# <a name="record-field-exchange-working-with-the-wizard-code"></a>Record Field Exchange : utilisation du code écrit par l'Assistant

> [!NOTE]
> L’Assistant Consommateur ODBC MFC n’est pas disponible dans Visual Studio 2019 et ultérieur. Vous pouvez toujours créer un consommateur manuellement.

Cette rubrique explique le code que les Assistants Application MFC et **Ajout de classe** (comme décrit dans [Ajout d’un consommateur ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) écrivent pour prendre en charge RFX et comment vous pouvez modifier ce code.

> [!NOTE]
> Cette rubrique s’applique aux classes dérivées de `CRecordset` où l’extraction de lignes en bloc n’a pas été implémentée. Si vous utilisez l’extraction de lignes en bloc, l’échange de champs d’enregistrements en bloc (Bulk RFX) est implémenté. Bulk RFX est similaire à RFX. Pour comprendre les différences, consultez [Recordset : extraction globale d’enregistrements (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Quand vous créez une classe recordset avec l’Assistant Application MFC ou **Ajout de classe**, l’Assistant écrit les éléments associés à RFX suivants pour vous, en fonction de la source de données, des tables et des colonnes que vous choisissez dans l’Assistant :

- Déclarations des membres de données de champ de recordset dans la classe recordset

- Un remplacement de `CRecordset::DoFieldExchange`

- Initialisation des membres de données de champ de recordset dans le constructeur de la classe recordset

## <a name="field-data-member-declarations"></a><a name="_core_the_field_data_member_declarations"></a> Déclarations des membres de données de champ

Les Assistants écrivent une déclaration de classe recordset dans un fichier .h qui ressemble à ce qui suit pour la classe `CSections` :

```cpp
class CSections : public CRecordset
{
public:
   CSections(CDatabase* pDatabase = NULL);
   DECLARE_DYNAMIC(CSections)

// Field/Param Data
   CString   m_strCourseID;
   CString   m_strInstructorID;
   CString   m_strRoomNo;
   CString   m_strSchedule;
   CString   m_strSectionNo;

// Overrides
   // Wizard generated virtual function overrides
   protected:
   virtual CString GetDefaultConnect();  // Default connection string
   virtual CString GetDefaultSQL();      // Default SQL for Recordset
   virtual void DoFieldExchange(CFieldExchange* pFX);  // RFX support

// Implementation
#ifdef _DEBUG
   virtual void AssertValid() const;
   virtual void Dump(CDumpContext& dc) const;
#endif

};
```

Si vous ajoutez des membres de données de paramètre ou de nouveaux membres de données de champ que vous liez vous-même, ajoutez-les après ceux générés par l’Assistant.

Remarquez également que l’Assistant substitue la fonction membre `DoFieldExchange` de la classe `CRecordset`.

## <a name="dofieldexchange-override"></a><a name="_core_the_dofieldexchange_override"></a> Remplacement de DoFieldExchange

[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) est au cœur de RFX. Le framework appelle `DoFieldExchange` quand il a besoin de déplacer des données depuis la source de données vers le recordset ou inversement. De plus, `DoFieldExchange` prend en charge l’obtention d’informations sur les membres de données de champ par le biais des fonctions membres [IsFieldDirty](../../mfc/reference/crecordset-class.md#isfielddirty) et [IsFieldNull](../../mfc/reference/crecordset-class.md#isfieldnull).

Le remplacement `DoFieldExchange` suivant concerne la classe `CSections`. L’Assistant écrit la fonction dans le fichier .cpp pour votre classe recordset.

```cpp
void CSections::DoFieldExchange(CFieldExchange* pFX)
{
   pFX->SetFieldType(CFieldExchange::outputColumn);
   RFX_Text(pFX, "CourseID", m_strCourseID);
   RFX_Text(pFX, "InstructorID", m_strInstructorID);
   RFX_Text(pFX, "RoomNo", m_strRoomNo);
   RFX_Text(pFX, "Schedule", m_strSchedule);
   RFX_Text(pFX, "SectionNo", m_strSectionNo);
}
```

Notez les fonctionnalités clés suivantes de la fonction :

- Cette section de la fonction est appelée mappage de champs.

- Un appel à `CFieldExchange::SetFieldType`, jusqu’au pointeur `pFX`. Cet appel indique que tous les appels de fonction RFX jusqu’à la fin de `DoFieldExchange` ou l’appel suivant à `SetFieldType` sont des colonnes de sortie. Pour plus d’informations, consultez [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype).

- Plusieurs appels à la fonction globale `RFX_Text`, à raison d’un par membre de données de champ (qui sont tous des variables `CString` dans l’exemple). Ces appels spécifient la relation entre un nom de colonne sur la source de données et un membre de données de champ. Les fonctions RFX effectuent le transfert de données proprement dit. La bibliothèque de classes fournit des fonctions RFX pour tous les types de données courants. Pour plus d’informations sur les fonctions RFX, consultez [Record Field Exchange : utilisation des fonctions RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md).

    > [!NOTE]
    >  L’ordre des colonnes dans votre jeu de résultats doit correspondre à l’ordre des appels de fonction RFX dans `DoFieldExchange`.

- Le pointeur `pFX` vers un objet [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) que le framework passe quand il appelle `DoFieldExchange`. L’objet `CFieldExchange` spécifie l’opération que doit effectuer `DoFieldExchange`, la direction de transfert et d’autres informations de contexte.

## <a name="recordset-constructor"></a><a name="_core_the_recordset_constructor"></a> Constructeur de recordset

Le constructeur de recordset écrit par l’Assistant contient deux éléments associés à RFX :

- Une initialisation de chaque membre de données de champ

- Une initialisation du membre de données [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields), qui contient le nombre de membres de données de champ

Le constructeur pour l’exemple de recordset `CSections` ressemble à ceci :

```cpp
CSections::CSections(CDatabase* pdb)
   : CRecordset(pdb)
{
   m_strCourseID = "";
   m_strInstructorID = "";
   m_strRoomNo = "";
   m_strSchedule = "";
   m_strSectionNo = "";
   m_nFields = 5;
}
```

> [!NOTE]
> Si vous ajoutez des membres de données de champ manuellement, comme vous le feriez pour lier de nouvelles colonnes dynamiquement, vous devez incrémenter `m_nFields`. Pour ce faire, ajoutez une autre ligne de code, par exemple :

```cpp
m_nFields += 3;
```

Ce code permet d’ajouter trois nouveaux champs. Si vous ajoutez des membres de données de paramètre, vous devez initialiser le membre de données [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams), qui contient le nombre de membres de données de paramètre. Placez l’initialisation `m_nParams` en dehors des accolades.

## <a name="see-also"></a>Voir aussi

[RFX (Record Field Exchange)](../../data/odbc/record-field-exchange-rfx.md)
