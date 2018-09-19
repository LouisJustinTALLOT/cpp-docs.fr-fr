---
title: Test du fournisseur en lecture seule | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- OLE DB providers, calling
- OLE DB providers, testing
ms.assetid: e4aa30c1-391b-41f8-ac73-5270e46fd712
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: aa56a62fa898f7ebe6c171af6f7246106b8e5ac7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038730"
---
# <a name="testing-the-read-only-provider"></a>Test du fournisseur accessible en lecture seule

Pour tester un fournisseur, vous avez besoin d’un consommateur. Il est utile si le consommateur à faire correspondre avec le fournisseur. Les modèles du consommateur OLE DB constituent un simple wrapper autour d’OLE DB et correspondent aux objets COM du fournisseur. Étant donné que la source est livrée avec les modèles du consommateur, il est facile de déboguer un fournisseur avec eux. Les modèles de consommateurs sont également un moyen très simple et rapide pour développer des applications grand public.  
  
L’exemple dans cette rubrique crée une application d’Assistant Application MFC par défaut pour un consommateur de test. L’application de test est ajouté un code de modèle du consommateur OLE DB, une boîte de dialogue simple.  
  
### <a name="to-create-the-test-application"></a>Pour créer l’application de test  
  
1. Dans le menu **Fichier** , cliquez sur **Nouveau**, puis sur **Projet**.  
  
1. Dans le volet Types de projets, sélectionnez le dossier **Projets Visual C++**. Dans le volet Modèles, sélectionnez **Application MFC**.  
  
1. Nom de projet, entrez **TestProv**, puis cliquez sur **OK**.  
  
     L’Assistant Application MFC s’affiche.  
  
1. Sur le **Type d’Application** page, sélectionnez **basée sur un dialogue**.  
  
1. Sur le **fonctionnalités avancées** page, sélectionnez **Automation**, puis cliquez sur **Terminer**.  
  
> [!NOTE]
>  L’application ne nécessite pas de prise en charge Automation si vous ajoutez **CoInitialize** dans **CTestProvApp::InitInstance**.  
  
Vous pouvez afficher et modifier la boîte de dialogue TestProv (IDD_TESTPROV_DIALOG) en la sélectionnant dans l’affichage des ressources. Placez les deux zones de liste, un pour chaque chaîne dans l’ensemble de lignes dans la boîte de dialogue. Désactiver la propriété de tri pour les deux zones de liste en appuyant sur ALT + ENTRÉE quand une zone de liste est sélectionnée, en cliquant sur le **Styles** onglet et en désactivant le **tri** case à cocher. En outre, placez un **exécuter** bouton dans la boîte de dialogue pour extraire le fichier. La boîte de dialogue TestProv terminée doit avoir deux zones de liste intitulées « String 1 » et « String 2 », respectivement. Il a également **OK**, **Annuler**, et **exécuter** boutons.  
  
Ouvrez le fichier d’en-tête pour la classe de boîte de dialogue (en l’occurrence TestProvDlg.h). Ajoutez le code suivant au fichier d’en-tête (en dehors de toutes les déclarations de classe) :  
  
```cpp
////////////////////////////////////////////////////////////////////////  
// TestProvDlg.h  
  
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
  
Le code représente un enregistrement utilisateur qui définit les colonnes seront dans l’ensemble de lignes. Lorsque le client appelle la méthode `IAccessor::CreateAccessor`, il utilise ces entrées pour spécifier les colonnes à lier. Les modèles du consommateur OLE DB vous permettent également de lier les colonnes dynamiquement. Les macros COLUMN_ENTRY sont la version côté client des macros PROVIDER_COLUMN_ENTRY. Les deux macros COLUMN_ENTRY spécifient l’ordinal, d’un membre de type, longueur et les données pour les deux chaînes.  
  
Ajouter une fonction gestionnaire pour le **exécuter** bouton en appuyant sur CTRL et en double-cliquant sur le **exécuter** bouton. Placez le code suivant dans la fonction :  
  
```cpp
///////////////////////////////////////////////////////////////////////  
// TestProvDlg.cpp  
  
void CtestProvDlg::OnRun()  
{  
   CCommand<CAccessor<CProvider>> table;  
   CDataSource source;  
   CSession   session;  
  
   if (source.Open("MyProvider.MyProvider.1", NULL) != S_OK)  
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
  
Le `CCommand`, `CDataSource`, et `CSession` classes appartiennent tous à des modèles du consommateur OLE DB. Chaque classe simule un objet COM dans le fournisseur. Le `CCommand` objet prend la `CProvider` classe, déclarée dans le fichier d’en-tête, comme un paramètre de modèle. Le `CProvider` paramètre représente les liaisons que vous utilisez pour accéder aux données à partir du fournisseur. Voici le `Open` code pour la source de données, la session et la commande :  
  
```cpp  
if (source.Open("MyProvider.MyProvider.1", NULL) != S_OK)  
   return;  
  
if (session.Open(source) != S_OK)  
   return;  
  
if (table.Open(session, _T("c:\\samples\\myprov\\myData.txt")) != S_OK)  
   return;  
```  
  
Les lignes pour ouvrir chacune des classes créent chaque objet COM dans le fournisseur. Pour localiser le fournisseur, utilisez le ProgID du fournisseur. Vous pouvez obtenir le ProgID à partir du Registre système ou en consultant le fichier MyProvider.rgs (ouvrez le répertoire et la recherche de la clé ProgID du fournisseur).  
  
Le fichier MyData.txt est inclus dans l’exemple MyProv. Pour créer un fichier de votre choix, utilisez un éditeur et tapez un nombre pair de chaînes, en appuyant sur entrée entre chaque chaîne. Modifiez le nom de chemin d’accès si vous déplacez le fichier.  
  
Passez la chaîne « c:\\\samples\\\myprov\\\MyData.txt » dans le `table.Open` ligne. Si vous parcourez le `Open` appel, vous voyez que cette chaîne est passée à la `SetCommandText` méthode dans le fournisseur. Notez que le `ICommandText::Execute` méthode utilisé cette chaîne.  
  
Pour extraire les données, appelez `MoveNext` sur la table. `MoveNext` appelle le `IRowset::GetNextRows`, `GetRowCount`, et `GetData` fonctions. Lorsqu’il n’y a plus aucune ligne (autrement dit, la position actuelle dans l’ensemble de lignes est supérieure à `GetRowCount`), la boucle se termine :  
  
```cpp  
while (table.MoveNext() == S_OK)  
{  
   m_ctlString1.AddString(table.szField1);  
   m_ctlString2.AddString(table.szField2);  
}  
```  
  
Notez que lorsqu’il n’y a plus aucune ligne, les fournisseurs retournent DB_S_ENDOFROWSET. La valeur DB_S_ENDOFROWSET n’est pas une erreur. Vous devez toujours vérifier par rapport à S_OK pour annuler une boucle d’extraction de données et de ne pas utiliser la macro SUCCEEDED.  
  
Vous devez maintenant être en mesure de générer et tester le programme.  
  
## <a name="see-also"></a>Voir aussi  

[Amélioration du fournisseur simple accessible en lecture seule](../../data/oledb/enhancing-the-simple-read-only-provider.md)