---
description: 'En savoir plus sur : test du fournisseur de Read-Only'
title: Test du fournisseur accessible en lecture seule
ms.date: 11/04/2016
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- OLE DB providers, calling
- OLE DB providers, testing
ms.assetid: e4aa30c1-391b-41f8-ac73-5270e46fd712
ms.openlocfilehash: 2fbe0e7fb67b83cae65848939fa63bce42dab173
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272693"
---
# <a name="testing-the-read-only-provider"></a>Test du fournisseur accessible en lecture seule

Pour tester un fournisseur, vous avez besoin d’un consommateur. Cela permet à l’utilisateur d’établir une correspondance avec le fournisseur. Les modèles de consommateur OLE DB sont un wrapper léger autour des OLE DB et correspondent aux objets COM du fournisseur. Étant donné que la source est fournie avec les modèles de consommateur, il est facile de déboguer un fournisseur avec eux. Les modèles de consommateurs sont également un moyen très court et rapide de développer des applications grand public.

L’exemple de cette rubrique crée une application d’Assistant Application MFC par défaut pour un consommateur de test. L’application de test est une boîte de dialogue simple avec OLE DB code du modèle de consommateur ajouté.

## <a name="to-create-the-test-application"></a>Pour créer l'application de test

1. Dans le menu **Fichier**, cliquez sur **Nouveau**, puis sur **Projet**.

1. Dans le volet **types de projets** , sélectionnez le dossier **installé**  >  **Visual C++**  >  **MFC/ATL** . Dans le volet **modèles** , sélectionnez **application MFC**.

1. Pour le nom du projet, entrez *TestProv*, puis cliquez sur **OK**.

   L’Assistant **application MFC** s’affiche.

1. Sur la page **type d’application** , sélectionnez basée sur une boîte de **dialogue**.

1. Dans la page **fonctionnalités avancées** , sélectionnez **Automation**, puis cliquez sur **Terminer**.

> [!NOTE]
> L’application ne nécessite pas de prise en charge d’Automation si vous ajoutez `CoInitialize` dans `CTestProvApp::InitInstance` .

Vous pouvez afficher et modifier la boîte de dialogue **TestProv** (IDD_TESTPROV_DIALOG) en la sélectionnant dans **affichage des ressources**. Placez deux zones de liste, une pour chaque chaîne de l’ensemble de lignes, dans la boîte de dialogue. Désactivez la propriété de tri pour les deux zones de liste en appuyant sur **ALT** + **entrée** quand une zone de liste est sélectionnée et en affectant à la propriété de **Tri** la **valeur false**. Placez également un bouton **exécuter** dans la boîte de dialogue pour extraire le fichier. La boîte de dialogue **TestProv** terminée doit comporter deux zones de liste intitulées « chaîne 1 » et « chaîne 2 », respectivement. Il contient également les boutons **OK**, **Annuler** et **exécuter** .

Ouvrez le fichier d’en-tête pour la classe dialog (dans ce cas TestProvDlg. h). Ajoutez le code suivant au fichier d’en-tête (en dehors des déclarations de classe) :

```cpp
////////////////////////////////////////////////////////////////////////
// TestProvDlg.h
#include <atldbcli.h>  

class CProvider
{
// Attributes
public:
   char   szField1[16];
   char   szField2[16];

   // Binding Maps
BEGIN_COLUMN_MAP(CProvider)
   COLUMN_ENTRY(1, szField1)
   COLUMN_ENTRY(2, szField2)
END_COLUMN_MAP()
};
```

Le code représente un enregistrement d’utilisateur qui définit les colonnes qui se trouvent dans l’ensemble de lignes. Lorsque le client appelle `IAccessor::CreateAccessor` , il utilise ces entrées pour spécifier les colonnes à lier. Les modèles de consommateur OLE DB vous permettent également de lier des colonnes dynamiquement. Les macros COLUMN_ENTRY sont la version côté client des macros PROVIDER_COLUMN_ENTRY. Les deux macros COLUMN_ENTRY spécifient l’ordinal, le type, la longueur et le membre de données des deux chaînes.

Ajoutez une fonction de gestionnaire pour le bouton **exécuter** en appuyant sur **CTRL** et en double-cliquant sur le bouton **exécuter** . Placez le code suivant dans la fonction :

```cpp
///////////////////////////////////////////////////////////////////////
// TestProvDlg.cpp

void CTestProvDlg::OnRun()
{
   CCommand<CAccessor<CProvider>> table;
   CDataSource source;
   CSession session;

   if (source.Open("Custom.Custom.1", NULL) != S_OK)
      return;

   if (session.Open(source) != S_OK)
      return;

   if (table.Open(session, _T("c:\\samples\\myprov\\myData.txt")) != S_OK)
      return;

   while (table.MoveNext() == S_OK)
   {
      m_ctlString1.AddString(table.szField1);
      m_ctlString2.AddString(table.szField2);
   }
}
```

Les `CCommand` `CDataSource` classes, et `CSession` appartiennent toutes aux modèles de consommateur OLE DB. Chaque classe reproduit un objet COM dans le fournisseur. L' `CCommand` objet prend la `CProvider` classe, déclarée dans le fichier d’en-tête, en tant que paramètre de modèle. Le `CProvider` paramètre représente des liaisons que vous utilisez pour accéder aux données à partir du fournisseur.

Les lignes permettant d’ouvrir chacune des classes créent chaque objet COM dans le fournisseur. Pour localiser le fournisseur, utilisez le `ProgID` du fournisseur. Vous pouvez obtenir le `ProgID` à partir du Registre système ou en consultant le fichier. RGS personnalisé (Ouvrez le répertoire du fournisseur et recherchez la `ProgID` clé).

Le fichier MyData.txt est inclus dans l' `MyProv` exemple. Pour créer un fichier, utilisez un éditeur et tapez un nombre pair de chaînes, en appuyant sur **entrée** entre chaque chaîne. Modifiez le nom du chemin d’accès si vous déplacez le fichier.

Transmettez la chaîne « c : \\ \Samples \\ \myprov \\\MyData.txt » dans la `table.Open` ligne. Si vous exécutez pas à pas l' `Open` appel, vous constatez que cette chaîne est passée à la `SetCommandText` méthode dans le fournisseur. Notez que la `ICommandText::Execute` méthode a utilisé cette chaîne.

Pour extraire les données, appelez `MoveNext` sur la table. `MoveNext` appelle les `IRowset::GetNextRows` `GetRowCount` fonctions, et `GetData` . Lorsqu’il n’y a plus de lignes (autrement dit, la position actuelle dans l’ensemble de lignes est supérieure à `GetRowCount` ), la boucle se termine.

Lorsqu’il n’y a plus de lignes, les fournisseurs retournent DB_S_ENDOFROWSET. La valeur de DB_S_ENDOFROWSET n’est pas une erreur. Vous devez toujours vérifier S_OK pour annuler une boucle d’extraction de données et ne pas utiliser la macro SUCCEEDED.

Vous devez maintenant être en mesure de générer et de tester le programme.

## <a name="see-also"></a>Voir aussi

[Amélioration du fournisseur de Read-Only simple](../../data/oledb/enhancing-the-simple-read-only-provider.md)
