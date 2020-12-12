---
description: 'En savoir plus sur : TN026 : les routines DDX et DDV'
title: 'TN026 : routines DDX et DDV'
ms.date: 06/28/2018
f1_keywords:
- DDX
- DDV
helpviewer_keywords:
- DDX (dialog data exchange), procedures
- TN026
- DDV (dialog data validation), procedures
ms.assetid: c2eba87a-4b47-4083-b28b-e2fa77dfb4c4
ms.openlocfilehash: 1e5c8d3679b7e91ad7f356c1e6f6badc61cdd46f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215701"
---
# <a name="tn026-ddx-and-ddv-routines"></a>TN026 : routines DDX et DDV

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Cette note décrit l’architecture d’échange de données de boîtes de dialogue (DDX) et de validation de données de boîtes de dialogue (DDV). Elle explique également comment écrire une procédure DDX_ ou DDV_ et comment vous pouvez étendre ClassWizard pour utiliser vos routines.

## <a name="overview-of-dialog-data-exchange"></a>Vue d’ensemble de l’échange de données de boîtes de dialogue

Toutes les fonctions de données de dialogue sont effectuées avec du code C++. Il n’existe aucune ressource spéciale ou macros magiques. Le cœur du mécanisme est une fonction virtuelle qui est substituée dans chaque classe de dialogue qui effectue l’échange et la validation des données de boîte de dialogue. Il se trouve toujours sous la forme suivante :

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

Les commentaires AFX de format spécial permettent à ClassWizard de localiser et de modifier le code dans cette fonction. Le code qui n’est pas compatible avec ClassWizard doit être placé en dehors des commentaires de format spéciaux.

Dans l’exemple ci-dessus, \<data_exchange_function_call> se présente sous la forme :

```cpp
DDX_Custom(pDX, nIDC, field);
```

et \<data_validation_function_call> est facultatif et se présente sous la forme suivante :

```cpp
DDV_Custom(pDX, field, ...);
```

Plusieurs paires DDX_/DDV_ peuvent être incluses dans chaque `DoDataExchange` fonction.

Consultez « afxdd_. h » pour obtenir la liste de toutes les routines d’échange de données de boîte de dialogue et les routines de validation de données de boîte de dialogue fournies avec MFC.

Les données de la boîte de dialogue sont simplement les données de membre de la `CMyDialog` classe. Elle n’est pas stockée dans un struct ou quelque chose de similaire.

## <a name="notes"></a>Remarques

Bien que nous appelons cette « données de boîte de dialogue », toutes les fonctionnalités sont disponibles dans toute classe dérivée de `CWnd` et ne sont pas limitées aux simples boîtes de dialogue.

Les valeurs initiales des données sont définies dans le constructeur C++ standard, généralement dans un bloc avec des `//{{AFX_DATA_INIT` `//}}AFX_DATA_INIT` commentaires et.

`CWnd::UpdateData` est l’opération qui effectue l’initialisation et la gestion des erreurs autour de l’appel à `DoDataExchange` .

Vous pouvez appeler `CWnd::UpdateData` à tout moment pour effectuer l’échange et la validation de données. Par défaut `UpdateData` (true) est appelé dans le gestionnaire par défaut `CDialog::OnOK` et `UpdateData` (false) est appelé dans la valeur par défaut `CDialog::OnInitDialog` .

La routine de DDV_ doit suivre immédiatement la routine DDX_ pour ce *champ*.

## <a name="how-does-it-work"></a>Comment cela fonctionne-t-il ?

Vous n’avez pas besoin de comprendre les éléments suivants pour pouvoir utiliser les données de boîte de dialogue. Toutefois, comprendre comment cela fonctionne en arrière-plan vous permet d’écrire votre propre procédure de validation ou d’échange.

La `DoDataExchange` fonction membre est semblable à la `Serialize` fonction membre. elle est chargée d’obtenir ou de définir des données vers/à partir d’un formulaire externe (dans ce cas, des contrôles dans une boîte de dialogue) de/vers les données de membre de la classe. Le paramètre *pDX* est le contexte de l’échange de données et est semblable au `CArchive` paramètre de `CObject::Serialize` . Le *pDX* (un `CDataExchange` objet) a un indicateur de direction similaire à `CArchive` un indicateur de direction :

- Si `!m_bSaveAndValidate` , puis chargez l’état des données dans les contrôles.

- Si la `m_bSaveAndValidate` valeur est, définissez l’état des données à partir des contrôles.

La validation se produit uniquement lorsque `m_bSaveAndValidate` est défini. La valeur de `m_bSaveAndValidate` est déterminée par le paramètre bool à `CWnd::UpdateData` .

Il existe trois autres `CDataExchange` membres intéressants :

- `m_pDlgWnd`: Fenêtre (généralement une boîte de dialogue) qui contient les contrôles. Cela permet d’empêcher les appelants des fonctions globales DDX_ et DDV_ de passer’This’à chaque routine DDX/DDV.

- `PrepareCtrl`, et `PrepareEditCtrl` : prépare un contrôle de boîte de dialogue pour l’échange de données. Stocke le handle de ce contrôle pour définir le focus en cas d’échec d’une validation. `PrepareCtrl` est utilisé pour les contrôles de non-modification et `PrepareEditCtrl` est utilisé pour les contrôles d’édition.

- `Fail`: Appelé après l’émission d’une boîte de message avertissant l’utilisateur de l’erreur d’entrée. Cette routine restaure le focus sur le dernier contrôle (le dernier appel à `PrepareCtrl` ou `PrepareEditCtrl` ) et lève une exception. Cette fonction membre peut être appelée à partir des routines DDX_ et DDV_.

## <a name="user-extensions"></a>Extensions utilisateur

Il existe plusieurs façons d’étendre le mécanisme DDX/DDV par défaut. Vous pouvez :

- Ajoutez de nouveaux types de données.

    ```cpp
    CTime
    ```

- Ajoutez de nouvelles procédures Exchange (DDX_).

    ```cpp
    void PASCAL DDX_Time(CDataExchange* pDX, int nIDC, CTime& tm);
    ```

- Ajoutez de nouvelles procédures de validation (DDV_).

    ```cpp
    void PASCAL DDV_TimeFuture(CDataExchange* pDX, CTime tm, BOOL bFuture);
    // make sure time is in the future or past
    ```

- Transmettez des expressions arbitraires aux procédures de validation.

    ```cpp
    DDV_MinMax(pDX, age, 0, m_maxAge);
    ```

    > [!NOTE]
    > Ces expressions arbitraires ne peuvent pas être modifiées par ClassWizard et doivent donc être déplacées en dehors des commentaires de format spéciaux (//{{AFX_DATA_MAP (CMyClass)).

Faire en sorte que la `DoDialogExchange` fonction membre comprenne des conditions ou toute autre instruction C++ valide avec des appels d’échange et de fonction de validation intermélangés.

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
> Comme indiqué ci-dessus, ce code ne peut pas être modifié par ClassWizard et doit être utilisé uniquement en dehors des commentaires de format spéciaux.

## <a name="classwizard-support"></a>Prise en charge de ClassWizard

ClassWizard prend en charge un sous-ensemble de personnalisations DDX/DDV en vous permettant d’intégrer vos propres routines DDX_ et DDV_ dans l’interface utilisateur de l’Assistant. Cela n’est utile que si vous envisagez de réutiliser des routines DDX et DDV particulières dans un projet ou dans de nombreux projets.

Pour ce faire, des entrées spéciales sont effectuées dans DDX. CLW (les versions précédentes de Visual C++ stockaient ces informations dans APSTUDIO.INI) ou dans le de votre projet. Fichier CLW. Les entrées spéciales peuvent être entrées dans la section [informations générales] du de votre projet. Fichier CLW ou dans la section [ExtraDDX] du fichier DDX. CLW dans le répertoire \Program Files\Microsoft Visual Studio\Visual C++ \Bin. Vous devrez peut-être créer le fichier DDX. CLW s’il n’existe pas déjà. Si vous envisagez d’utiliser les routines de DDX_/DDV_ personnalisées uniquement dans un certain projet, ajoutez les entrées à la section [informations générales] de votre projet. Fichier CLW à la place. Si vous envisagez d’utiliser les routines sur de nombreux projets, ajoutez les entrées à la section [ExtraDDX] de DDX. CLW.

Le format général de ces entrées spéciales est le suivant :

> ExtraDDXCount =*n*

où *n* est le nombre de ExtraDDX ? lignes à suivre, sous la forme

> ExtraDDX ? =*clés*; *clés VB*; *invite de commandes*; *type*; *initValue*; *DDX_Proc* [; *DDV_Proc*; *prompt1*; *Arg1* [; *prompt2*; *fmt2*]]

Cela? est un nombre 1- *n* indiquant le type DDX de la liste qui est définie.

Chaque champ est délimité par un caractère « ; ». Les champs et leurs objectifs sont décrits ci-dessous.

- *légende*

  Liste de caractères uniques indiquant pour Quels contrôles de boîte de dialogue ce type de variable est autorisé.

  |Caractère|Contrôle autorisé|
  |-|-|
  E | modifier
  C | case à cocher à deux États
  c | case à cocher à trois États
  R | première case d’option dans un groupe
  L | zone de liste non triée
  l | zone de liste triée
  M | zone de liste déroulante (avec modification de l’élément)
  N | liste déroulante non triée
  n | liste déroulante triée
  1 | Si l’insertion DDX doit être ajoutée au début de liste (la valeur par défaut est ajouter à la fin), elle est généralement utilisée pour les routines DDX qui transfèrent la propriété « contrôle ».

- *clés VB*

  Ce champ est utilisé uniquement dans le produit 16 bits pour les contrôles VBX (les contrôles VBX ne sont pas pris en charge dans le produit 32 bits)

- *prompt*

  Chaîne à placer dans la zone de liste déroulante des propriétés (sans guillemets)

- *type*

  Identificateur unique pour le type à émettre dans le fichier d’en-tête. Dans l’exemple ci-dessus avec DDX_Time, cette valeur est définie sur CTime.

- *clés VB*

  Non utilisé dans cette version et doit toujours être vide

- *initValue*

  Valeur initiale : 0 ou vide. Si elle est vide, aucune ligne d’initialisation n’est écrite dans la section//{{AFX_DATA_INIT du fichier d’implémentation. Une entrée vide doit être utilisée pour les objets C++ (tels que `CString` , `CTime` , etc.) qui ont des constructeurs qui garantissent une initialisation correcte.

- *DDX_Proc*

  Identificateur unique de la procédure DDX_. Le nom de la fonction C++ doit commencer par « DDX_ », mais n’incluez pas « DDX_ » dans l' \<DDX_Proc> identificateur. Dans l’exemple ci-dessus, l' \<DDX_Proc> identificateur est Time. Lorsque ClassWizard écrit l’appel de fonction dans le fichier d’implémentation dans la section {{AFX_DATA_MAP, il ajoute ce nom à DDX_, arrivant donc à DDX_Time.

- *Commentaire*

  Commentaire à afficher dans la boîte de dialogue de la variable avec ce DDX. Placez le texte que vous souhaitez ici et fournissez généralement un nom qui décrit l’opération effectuée par la paire DDX/DDV.

- *DDV_Proc*

  La partie DDV de l’entrée est facultative. Toutes les routines DDX n’ont pas de routines DDV correspondantes. Souvent, il est plus commode d’inclure la phase de validation comme une partie intégrante du transfert. C’est souvent le cas lorsque votre routine DDV ne requiert pas de paramètres, car ClassWizard ne prend pas en charge les routines DDV sans aucun paramètre.

- *donnée*

  Identificateur unique de la procédure DDV_. Le nom de la fonction C++ doit commencer par « DDV_ », mais n’inclut pas « DDX_ » dans l' \<DDX_Proc> identificateur.

  *arg* est suivi de 1 ou 2 arguments DDV :

  - *invite*

      Chaîne à placer au-dessus de l’élément de modification (avec & pour l’accélérateur).

  - *fmtN*

      Caractère de format pour le type ARG, l’un des éléments suivants :

      |Caractère|Type|
      |-|-|
      |d | int|
      |u | nombre entier non signé|
      |D | long int (autrement dit, long)|
      |U | long non signé (c’est-à-dire, DWORD)|
      |f | float|
      |F | double|
      |s | string|

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
