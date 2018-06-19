---
title: 'TN026 : Routines DDX et DDV | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 44a946b21908f45b595056a956c75b234fdbb886
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33386052"
---
# <a name="tn026-ddx-and-ddv-routines"></a>TN026 : routines DDX et DDV
> [!NOTE]
>  La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.  
  
 Cette note décrit l’échange de données de boîtes de dialogue (DDX) et l’architecture de validation (DDV) de données de boîte de dialogue. Elle décrit également la façon dont vous écrivez une procédure DDX_ ou DDX_ et comment vous pouvez étendre ClassWizard pour utiliser vos routines.  
  
## <a name="overview-of-dialog-data-exchange"></a>Vue d’ensemble de l’échange de données de boîtes de dialogue  
 Toutes les fonctions de données de boîtes de dialogue sont effectuées avec le code C++. Il n’existe aucune des ressources particulières ou des macros magiques. Le cœur du mécanisme est une fonction virtuelle substituée dans chaque classe de boîte de dialogue que boîte de dialogue d’échange de données et la validation. Il existe toujours dans cet écran :  
  
```  
void CMyDialog::DoDataExchange(CDataExchange* pDX)  
{  
    CDialog::DoDataExchange(pDX);
*// call base class  
 *//{{AFX_DATA_MAP(CMyDialog)  
 <data_exchange_function_call>  
 <data_validation_function_call> *//}}AFX_DATA_MAP  
}  
```  
  
 Les commentaires AFX format spécial autoriser ClassWizard localiser et modifier le code dans cette fonction. Code qui n’est pas compatible avec ClassWizard doit être placé en dehors de commentaires spéciaux de format.  
  
 Dans l’exemple ci-dessus, < data_exchange_function_call > se présente sous la forme :  
  
```  
DDX_Custom(pDX,
    nIDC,
    field);
```  
  
 et < data_validation_function_call > est facultatif et se trouve dans le formulaire :  
  
```  
DDV_Custom(pDX,
    field, ...);
```  
  
 Plusieurs paires DDX_/DDX_ peut être inclus dans chaque `DoDataExchange` (fonction).  
  
 Pour obtenir la liste de toutes les routines d’échange de données de boîte de dialogue et les routines de validation de données de boîte de dialogue fournis avec MFC, consultez « afxdd_.h ».  
  
 C’est ce que les données de boîte de dialogue : données de membre dans le **CMyDialog** classe. Il n’est pas stocké dans un struct ou autres.  
  
## <a name="notes"></a>Notes  
 Bien que nous appelons cette « données de la boîte de dialogue », toutes les fonctionnalités sont disponibles dans n’importe quelle classe dérivée de `CWnd` et ne sont pas limités à simplement les boîtes de dialogue.  
  
 Les valeurs initiales des données sont définies dans le constructeur C++ standard, généralement dans un bloc avec `//{{AFX_DATA_INIT` et `//}}AFX_DATA_INIT` commentaires.  
  
 `CWnd::UpdateData` est l’opération qui effectue l’initialisation et leur gestion autour de l’appel à `DoDataExchange`.  
  
 Vous pouvez appeler `CWnd::UpdateData` à tout moment pour effectuer l’échange de données et la validation. Par défaut `UpdateData`(TRUE) est appelée dans la valeur par défaut `CDialog::OnOK` gestionnaire et `UpdateData`(FALSE) est appelée dans la valeur par défaut `CDialog::OnInitDialog`.  
  
 La routine DDX_ doit suivre immédiatement la routine DDX_ pour qui *champ*.  
  
## <a name="how-does-it-work"></a>Comment cela fonctionne-t-il  
 Vous n’avez pas besoin de comprendre les éléments suivants pour pouvoir utiliser les données de la boîte de dialogue. Toutefois, comprendre comment cela fonctionne en arrière-plan sera vous aider à écrire votre propre procédure de validation ou d’exchange.  
  
 Le `DoDataExchange` fonction membre est très semblable à la `Serialize` la fonction membre - il est responsable de l’obtention ou la définition des données vers/à partir d’un formulaire externe (dans ce cas contrôles dans une boîte de dialogue) à partir de/vers des données membres dans la classe. Le `pDX` paramètre constitue le contexte de l’opération d’échange de données et est semblable à la `CArchive` paramètre `CObject::Serialize`. Le `pDX` (un `CDataExchange` objet) a une direction d’indicateur comme `CArchive` a un indicateur de direction :  
  
-   Si **! m_bSaveAndValidate**, puis de charger l’état des données dans les contrôles.  
  
-   Si `m_bSaveAndValidate`, puis définissez l’état des données à partir des contrôles.  
  
 La validation se produit uniquement lorsque `m_bSaveAndValidate` est défini. La valeur de `m_bSaveAndValidate` est déterminé par le paramètre BOOL `CWnd::UpdateData`.  
  
 Il existe trois autres intéressants `CDataExchange` membres :  
  
- `m_pDlgWnd`: La fenêtre (généralement une boîte de dialogue) qui contient les contrôles. Cela consiste à empêcher les appelants des fonctions DDX_ et DDX_ globales à partir de 'this' passer chaque routine DDX/DDV.  
  
- `PrepareCtrl`, et `PrepareEditCtrl`: prépare un contrôle de boîte de dialogue pour l’échange de données. Stocke le handle de ce contrôle pour définir le focus si une validation échoue. `PrepareCtrl` est utilisé pour les contrôles nonedit et `PrepareEditCtrl` est utilisé pour les contrôles d’édition.  
  
- **Échec de**: appelé après avoir ajouté une boîte de message d’alerte de l’utilisateur de l’erreur d’entrée. Cette routine restaure le focus vers le dernier contrôle (le dernier appel à `PrepareCtrl` / `PrepareEditCtrl`) et lève une exception. Cette fonction membre peut être appelée à partir de routines DDX_ et DDX_.  
  
## <a name="user-extensions"></a>Extensions de l’utilisateur  
 Il existe plusieurs façons d’étendre le mécanisme DDX/DDV par défaut. Vous pouvez :  
  
-   Ajouter de nouveaux types de données.  
  
 ```  
    CTime 
 ```  
  
-   Ajouter de nouvelles procédures exchange (DDX_).  
  
 ```  
    void PASCAL DDX_Time(CDataExchange* pDX,
    int nIDC,
    CTime& tm);

 ```  
  
-   Ajouter de nouvelles procédures de validation (DDX_).  
  
 ```  
    void PASCAL DDV_TimeFuture(CDataExchange* pDX,
    CTime tm,
    BOOL bFuture);
*// make sure time is in the future or past  
 ```  
  
-   Passer des expressions arbitraires pour les procédures de validation.  
  
 ```  
    DDV_MinMax(pDX,
    age,
    0,
    m_maxAge);

 ```  
  
    > [!NOTE]
    >  Ces expressions arbitraires ne sont pas modifiables par ClassWizard et par conséquent doit être déplacées en dehors de commentaires spéciaux format (/ / {{AFX_DATA_MAP(CMyClass)).  
  
 Avoir le **DoDialogExchange** fonction membre incluent des instructions conditionnelles ou toute autre instruction C++ valide avec des appels de fonction échange et validation mélangés.  
  
```  
//{{AFX_DATA_MAP(CMyClass)  
DDX_Check(pDX,
    IDC_SEX,
    m_bFemale);

DDX_Text(pDX,
    IDC_EDIT1,
    m_age);

//}}AFX_DATA_MAP  
if (m_bFemale)  
    DDV_MinMax(pDX,
    age,
    0,
    m_maxFemaleAge);

else  
    DDV_MinMax(pDX,
    age,
    0,
    m_maxMaleAge);
```  
  
> [!NOTE]
>  Comme indiqué ci-dessus, ce code ne peut pas être modifié par ClassWizard et doit être utilisé uniquement en dehors de commentaires spéciaux de format.  
  
## <a name="classwizard-support"></a>Prise en charge de l’Assistant classe  
 ClassWizard prend en charge un sous-ensemble des personnalisations de DDX/DDV en vous permettant d’intégrer vos propres routines DDX_ et DDX_ dans l’interface utilisateur de ClassWizard. Cela est bénéfique de coût uniquement si vous projetez de réutiliser des routines DDX et DDV particuliers dans un projet ou dans de nombreux projets.  
  
 Pour ce faire, les entrées spéciales sont effectuées dans DDX. CLW (les versions précédentes de Visual C++ stockées ces informations dans APSTUDIO. INI) ou de votre projet. Fichier CLW. Les entrées spéciales peuvent être entré dans la section [général Info] de votre projet. Fichier CLW ou dans la section [ExtraDDX] de la DDX. Fichier CLW dans le répertoire C ++ \bin \Program Files\Microsoft Studio\Visual Visual. Vous devrez peut-être créer la DDX. Fichier CLW s’il n’existe pas. Si vous envisagez d’utiliser les routines DDX_/DDX_ personnalisés uniquement dans un projet donné, ajoutez les entrées à la section [général Info] de votre projet. CLW du fichier à la place. Si vous envisagez d’utiliser les routines de nombreux projets, ajoutez les entrées à la section [ExtraDDX] de DDX. CLW.  
  
 Le format général de ces entrées spéciales est :  
  
```  
ExtraDDXCount=n  
```  
  
 où n est le nombre de lignes ExtraDDX à suivre  
  
```  
ExtraDDX=<keys>;<vb-keys>; <prompt>; <type>; <initValue>; <DDX_Proc>  
[;<DDV_Proc>; <prompt1>; <arg1>; [<prompt2>; <fmt2>]]  
```  
  
 où est le nombre 1 - n qui indique le type DDX dans la liste qui est défini.  
  
 Chaque champ est délimitée par un caractère « ; ». Les champs et leur objectif sont décrits ci-dessous.  
  
 \<clés >  
 = liste de caractères uniques indiquant pour les contrôles de boîte de dialogue, ce type de variable est autorisé.  
  
 E = Édition  
  
 C = la case à cocher de deux États  
  
 c = la case à cocher à trois États  
  
 R = la première case d’option dans un groupe  
  
 L = la zone de liste non triée  
  
 l = la zone de liste triée  
  
 M = la zone de liste déroulante (avec l’élément de modification)  
  
 N = liste non triée  
  
 n = liste triée  
  
 1 = si l’insertion DDX doit être ajoutée au début de liste (valeur par défaut est ajouter à la fin du) cela est généralement utilisé pour les routines DDX chargés de transférer la propriété « Contrôle ».  
  
 \<clés de VB >  
 Ce champ est utilisé uniquement dans le produit de 16 bits pour les contrôles VBX (les contrôles VBX ne sont pas pris en charge dans le produit 32 bits)  
  
 \<invite >  
 Chaîne à placer dans la zone de liste déroulante de propriété (sans guillemets)  
  
 \<type>  
 Identificateur unique pour le type à émettre dans le fichier d’en-tête. Dans notre exemple ci-dessus avec DDX_Time, cela serait défini à CTime.  
  
 \<clés de VB >  
 Pas utilisé dans cette version et doit toujours être vide  
  
 \<Valeur >  
 Valeur initiale : 0 ou vide. Si elle est vide, aucune ligne d’initialisation n’est écrit dans la section //{{AFX_DATA_INIT du fichier d’implémentation. Une entrée vide doit être utilisée pour les objets C++ (tel que `CString`, `CTime`, et ainsi de suite) qui possèdent des constructeurs qui garantissent l’initialisation correcte.  
  
 < DDX_Proc >  
 Identificateur unique pour la procédure DDX_. Le nom de la fonction C++ doit commencer par « DDX_ », mais ne pas inclure « DDX_ » dans l’identificateur de < DDX_Proc >. Dans l’exemple ci-dessus, l’identificateur de < DDX_Proc > peut être. Lorsque ClassWizard écrit l’appel de fonction pour le fichier d’implémentation dans les {{section AFX_DATA_MAP, il ajoute ce nom à DDX_, donc arrivant à DDX_Time.  
  
 \<commentaire >  
 Commentaire à afficher dans la boîte de dialogue pour la variable avec cette DDX. Placez tout vous aimeriez ici et souvent fournir un élément de texte qui décrit l’opération effectuée par la paire de DDX/DDV.  
  
 < DDV_Proc >  
 La partie DDV de l’entrée est facultative. Pas toutes les routines de DDX ont des routines DDV correspondants. Il est souvent plus commode d’inclure la phase de validation en tant que partie intégrante du transfert. Cela est souvent le cas lorsque votre routine DDV ne nécessite pas de paramètres, étant donné que ClassWizard ne prend pas en charge les routines DDV sans aucun paramètre.  
  
 \<arg >  
 Identificateur unique pour la procédure DDX_. Le nom de la fonction C++ doit commencer par « DDX_ », mais n’incluez pas de « DDX_ » dans l’identificateur de < DDX_Proc >.  
  
 suivi des arguments DDV 1 ou 2 :  
  
 \<promptX >  
 chaîne à placer au-dessus de l’élément de modification (avec & pour l’accélérateur)  
  
 \<fmtX >  
 caractère de format pour le type d’argument, un des  
  
 d = int  
  
 u = non signé  
  
 D = long int (autrement dit, long)  
  
 U = long non signé (autrement dit, DWORD)  
  
 f = float  
  
 F = double  
  
 s = chaîne  
  
## <a name="see-also"></a>Voir aussi  
 [Notes techniques par numéro](../mfc/technical-notes-by-number.md)   
 [Notes techniques par catégorie](../mfc/technical-notes-by-category.md)

