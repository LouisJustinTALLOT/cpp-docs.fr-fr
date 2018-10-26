---
title: 'TN026 : Routines DDX et DDV | Microsoft Docs'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- DDX
- DDV
dev_langs:
- C++
helpviewer_keywords:
- DDX (dialog data exchange), procedures
- TN026
- DDV (dialog data validation), procedures
ms.assetid: c2eba87a-4b47-4083-b28b-e2fa77dfb4c4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f07ab7b4420a5c33be56a9278b60afb6424e9e83
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50063547"
---
# <a name="tn026-ddx-and-ddv-routines"></a>TN026 : routines DDX et DDV

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Cette note décrit l’échange de données de boîtes de dialogue (DDX) et l’architecture de validation (DDV) de données de boîte de dialogue. Elle décrit également la façon dont vous écrivez une procédure DDX_ ou DDX_ et comment vous pouvez étendre ClassWizard pour utiliser vos routines.

## <a name="overview-of-dialog-data-exchange"></a>Vue d’ensemble de l’échange de données de boîtes de dialogue

Toutes les fonctions de données de boîtes de dialogue sont effectuées avec le code C++. Il n’existe aucune des ressources spéciales ou des macros magiques. Le cœur du mécanisme est une fonction virtuelle qui est remplacée dans chaque classe de boîte de dialogue que boîte de dialogue d’échange de données et la validation. Il existe toujours dans ce formulaire :

```cpp
void CMyDialog::DoDataExchange(CDataExchange* pDX)
{
    CDialog::DoDataExchange(pDX);   // call base class

    //{{AFX_DATA_MAP(CMyDialog)
        <data_exchange_function_call>
        <data_validation_function_call>
    //}}AFX_DATA_MAP
}
```

Les commentaires AFX format spécial autoriser ClassWizard localiser et modifier le code au sein de cette fonction. Code qui n’est pas compatible avec ClassWizard doit être placé en dehors des commentaires de formats spéciaux.

Dans l’exemple ci-dessus, \<data_exchange_function_call > se présente sous la forme :

```cpp
DDX_Custom(pDX, nIDC, field);
```

et \<data_validation_function_call > est facultatif et se présente sous la forme :

```cpp
DDV_Custom(pDX, field, ...);
```

Plusieurs paires DDX_/DDX_ peut être inclus dans chaque `DoDataExchange` (fonction).

Pour obtenir la liste de toutes les routines d’échange de données de boîte de dialogue et les routines de validation de données de boîte de dialogue fournis avec MFC, consultez « afxdd_.h ».

C’est ce que les données de boîte de dialogue : données membres dans la `CMyDialog` classe. Il n’est pas stocké dans un struct ou quoi que ce soit similaire.

## <a name="notes"></a>Notes

Bien que nous appelons cette « données de boîte de dialogue », toutes les fonctionnalités sont disponibles dans n’importe quelle classe dérivée de `CWnd` et ne sont pas limités à des boîtes de dialogue simples.

Les valeurs initiales de données sont définies dans le constructeur C++ standard, généralement dans un bloc avec `//{{AFX_DATA_INIT` et `//}}AFX_DATA_INIT` commentaires.

`CWnd::UpdateData` est l’opération qui effectue l’initialisation et la gestion des autour de l’appel à erreurs `DoDataExchange`.

Vous pouvez appeler `CWnd::UpdateData` à tout moment pour effectuer l’échange de données et la validation. Par défaut `UpdateData`(TRUE) est appelée dans la valeur par défaut `CDialog::OnOK` gestionnaire et `UpdateData`(FALSE) est appelée dans la valeur par défaut `CDialog::OnInitDialog`.

La routine DDX_ doit suivre immédiatement la routine DDX_ pour qui *champ*.

## <a name="how-does-it-work"></a>Comment cela fonctionne-t-il

Vous n’avez pas besoin de comprendre ce qui suit pour utiliser les données de la boîte de dialogue. Toutefois, comprendre comment cela fonctionne en arrière-plan sera vous aider à écrire votre propre procédure exchange ou de validation.

Le `DoDataExchange` fonction membre est très similaire à la `Serialize` fonction membre - il est responsable de l’obtention ou définition de données vers/à partir d’un formulaire externe (dans ce cas contrôles dans une boîte de dialogue) à partir de/vers les données de membre dans la classe. Le *pDX* paramètre est le contexte qui permet d’effectuer l’échange de données et est semblable à la `CArchive` paramètre `CObject::Serialize`. Le *pDX* (un `CDataExchange` objet) a une direction d’indicateur comme `CArchive` a un indicateur de direction :

- Si `!m_bSaveAndValidate`, puis charger l’état des données dans les contrôles.

- Si `m_bSaveAndValidate`, puis définissez l’état des données à partir des contrôles.

La validation se produit uniquement lorsque `m_bSaveAndValidate` est défini. La valeur de `m_bSaveAndValidate` est déterminé par le paramètre BOOL vers `CWnd::UpdateData`.

Il existe trois autres intéressantes `CDataExchange` membres :

- `m_pDlgWnd`: La fenêtre (généralement une boîte de dialogue) qui contient les contrôles. Cela vise à éviter des appelants des fonctions DDX_ et DDX_ globales de devoir passer 'this' à chaque routine DDX/DDV.

- `PrepareCtrl`, et `PrepareEditCtrl`: prépare un contrôle de boîte de dialogue pour l’échange de données. Stocke le handle de ce contrôle pour définir le focus si une validation échoue. `PrepareCtrl` est utilisé pour les contrôles d’édition non et `PrepareEditCtrl` est utilisé pour les contrôles d’édition.

- `Fail`: Appelée après avoir ajouté une boîte de message d’alerte de l’utilisateur à l’erreur d’entrée. Cette routine restaurez le focus sur le dernier contrôle (le dernier appel à `PrepareCtrl` ou `PrepareEditCtrl`) et lève une exception. Cette fonction membre peut être appelée à partir de routines DDX_ et DDX_.

## <a name="user-extensions"></a>Extensions de l’utilisateur

Il existe plusieurs façons d’étendre le mécanisme DDX/DDV par défaut. Vous pouvez :

- Ajouter de nouveaux types de données.

    ```cpp
    CTime
    ```

- Ajouter de nouvelles procédures exchange (DDX_).

    ```cpp
    void PASCAL DDX_Time(CDataExchange* pDX, int nIDC, CTime& tm);
    ```

- Ajouter de nouvelles procédures de validation (DDX_).

    ```cpp
    void PASCAL DDV_TimeFuture(CDataExchange* pDX, CTime tm, BOOL bFuture);
    // make sure time is in the future or past
    ```

- Passer des expressions arbitraires pour les procédures de validation.

    ```cpp
    DDV_MinMax(pDX, age, 0, m_maxAge);
    ```

    > [!NOTE]
    > Ces expressions arbitraires ne sont pas modifiables par ClassWizard et par conséquent doit être déplacées en dehors des commentaires de formats spéciaux (/ / {{AFX_DATA_MAP(CMyClass)).

Avoir le `DoDialogExchange` fonction membre incluent des instructions conditionnelles ou toute autre instruction C++ valide avec des appels de fonction échange et validation mélangés.

```cpp
//{{AFX_DATA_MAP(CMyClass)
DDX_Check(pDX, IDC_SEX, m_bFemale);
DDX_Text(pDX, IDC_EDIT1, m_age);
//}}AFX_DATA_MAP
if (m_bFemale)
    DDV_MinMax(pDX, age, 0, m_maxFemaleAge);
else
    DDV_MinMax(pDX, age, 0, m_maxMaleAge);
```

> [!NOTE]
> Comme indiqué ci-dessus, ce code ne peut pas être modifié par ClassWizard et doit être utilisé uniquement en dehors des commentaires de formats spéciaux.

## <a name="classwizard-support"></a>Prise en charge ClassWizard

ClassWizard prend en charge un sous-ensemble des personnalisations de DDX/DDV en vous permettant d’intégrer vos propres routines DDX_ et DDX_ dans l’interface utilisateur de ClassWizard. Cette opération d’est le seul coût avantageux si vous projetez de réutiliser des routines DDX et DDV particuliers dans un projet ou dans de nombreux projets.

Pour ce faire, les entrées particulières sont effectuées dans DDX. CLW (les versions précédentes de Visual C++ stocké ces informations dans APSTUDIO. INI) ou dans votre projet. Fichier CLW. Les entrées spéciales peuvent être entré dans la section [général Info] de votre projet. Fichier CLW ou dans la section [ExtraDDX] de la DDX. Fichier CLW dans le répertoire de \bin C ++ Visual Studio\Visual \Program Files\Microsoft. Vous devrez peut-être créer le DDX. Fichier CLW s’il n’existe pas déjà. Si vous envisagez d’utiliser les routines DDX_/DDX_ personnalisés uniquement dans un projet donné, ajoutez les entrées à la section [général Info] de votre projet. CLW du fichier à la place. Si vous envisagez d’utiliser les routines sur de nombreux projets, ajoutez les entrées à la section [ExtraDDX] de DDX. CLW.

Le format général de ces entrées spéciales est :

> ExtraDDXCount =*n*

où *n* est le nombre de ExtraDDX ? lignes à suivre, sous la forme

> ExtraDDX ? =*clés*; *vb-clés*; *invite*; *type*; *initialisation*; *DDX_Proc* [ ; *DDV_Proc*; *prompt1*; *arg1* [ ; *prompt2*; *fmt2*]]

où ? est un nombre 1 - *n* qui indique le type DDX dans la liste qui est défini.

Chaque champ est délimitée par un caractère « ; ». Les champs et leur objectif sont décrits ci-dessous.

- *Clés*

  Une liste de caractères uniques indiquant pour les contrôles de boîte de dialogue ce type de variable est autorisé.

  |Caractère|Contrôle autorisé|
  |-|-|
  E | modifier
  C | case à cocher deux États
  c | case à cocher à trois États
  R | premier bouton de case d’option dans un groupe
  L | zone de liste non triée
  l | zone de liste triée
  M | zone de liste déroulante (avec l’élément d’édition)
  N | liste non triée
  n | liste triée
  1 | Si l’insertion DDX doit être ajoutée à la tête de liste (par défaut est d’ajouter à la fin du) il est généralement utilisé pour les routines DDX que transférer la propriété « Contrôle ».

- *clés de VB*

  Ce champ est utilisé uniquement dans le produit de 16 bits pour les contrôles VBX (les contrôles VBX ne sont pas pris en charge dans le produit de 32 bits)

- *prompt*

  Chaîne à placer dans la zone de liste déroulante de propriété (sans guillemets)

- *type*

  Identificateur unique pour le type à émettre dans le fichier d’en-tête. Dans notre exemple ci-dessus avec DDX_Time, cela serait défini à CTime.

- *clés de VB*

  Pas utilisé dans cette version et doit toujours être vide

- *Initialisation*

  Valeur initiale : 0 ou vide. Si elle est vide, aucune ligne d’initialisation n’est écrit dans la section //{{AFX_DATA_INIT du fichier d’implémentation. Une entrée vide doit être utilisée pour les objets C++ (tel que `CString`, `CTime`, et ainsi de suite) qui possèdent des constructeurs qui garantissent l’initialisation correcte.

- *DDX_Proc*

  Identificateur unique pour la procédure DDX_. Le nom de la fonction C++ doit commencer par « DDX_ », mais n’incluez pas « DDX_ » dans le \<DDX_Proc > identificateur. Dans l’exemple ci-dessus, le \<DDX_Proc > identificateur serait le temps. Quand ClassWizard écrit l’appel de fonction pour le fichier d’implémentation dans les {{section AFX_DATA_MAP, il ajoute ce nom à DDX_, par conséquent arrivant à DDX_Time.

- *commentaire*

  Commentaire à afficher dans la boîte de dialogue pour la variable avec ce DDX. Placez tout texte que vous souhaitez que d’ici et généralement fournir quelque chose qui décrit l’opération exécutée par la paire DDX/DDV.

- *DDV_Proc*

  La partie DDV de l’entrée est facultative. Pas toutes les routines DDX ont des routines DDV correspondantes. Souvent, il est plus commode d’inclure la phase de validation comme partie intégrante du transfert. Cela est souvent le cas lorsque votre routine DDV ne nécessite pas de paramètres, étant donné que ClassWizard ne prend pas en charge les routines DDV sans aucun paramètre.

- *arg*

  Identificateur unique pour la procédure DDX_. Le nom de la fonction C++ doit commencer par « DDX_ », mais n’incluez pas « DDX_ » dans le \<DDX_Proc > identificateur.

  *arg* suivie de 1 ou 2 args DDV :

   - *promptN*

      Chaîne à placer au-dessus de l’élément d’édition (en & pour accélérateur).

   - *fmtN*

      Caractère de format pour le type arg, une des :

      |Caractère|Type|
      |-|-|
      |d | int|
      |u | unsigned int|
      |D | long int (autrement dit, long)|
      |U | long non signé (autrement dit, DWORD)|
      |f | float|
      |F | double|
      |s | chaîne|

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
