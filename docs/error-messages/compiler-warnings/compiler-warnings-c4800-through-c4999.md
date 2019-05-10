---
title: Avertissements du compilateur C4800 à C5999
ms.date: 04/21/2019
f1_keywords:
- C4808
- C4809
- C4825
- C4827
- C4837
- C4841
- C4842
- C4843
- C4844
- C4845
- C4846
- C4847
- C4848
- C4872
- C4880
- C4881
- C4882
- C4910
- C4916
- C4921
- C4934
- C4951
- C4954
- C4955
- C4963
- C4966
- C4970
- C4971
- C4973
- C4974
- C4981
- C4985
- C4987
- C4988
- C4989
- C4990
- C4991
- C4992
- C4998
- C5022
- C5023
- C5024
- C5025
- C5026
- C5027
- C5028
- C5029
- C5030
- C5031
- C5032
- C5033
- C5034
- C5035
- C5036
- C5037
- C5039
- C5040
- C5041
- C5042
- C5043
- C5044
- C5045
- C5046
- C5047
- C5048
- C5049
- C5050
- C5100
- C5101
- C5102
- C5103
- C5104
- C5105
- C5106
- C5107
helpviewer_keywords:
- C4808
- C4809
- C4825
- C4827
- C4837
- C4841
- C4842
- C4843
- C4844
- C4845
- C4846
- C4847
- C4848
- C4872
- C4880
- C4881
- C4882
- C4910
- C4916
- C4921
- C4934
- C4951
- C4954
- C4955
- C4963
- C4966
- C4970
- C4971
- C4973
- C4974
- C4981
- C4985
- C4987
- C4988
- C4989
- C4990
- C4991
- C4992
- C4998
- C5022
- C5023
- C5024
- C5025
- C5026
- C5027
- C5028
- C5029
- C5030
- C5031
- C5032
- C5033
- C5034
- C5035
- C5036
- C5037
- C5039
- C5040
- C5041
- C5042
- C5043
- C5044
- C5045
- C5046
- C5047
- C5048
- C5049
- C5050
- C5100
- C5101
- C5102
- C5103
- C5104
- C5105
- C5106
- C5107
ms.openlocfilehash: 93ff809d640efab6852e855f85e7b6e0109d9c1d
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857448"
---
# <a name="compiler-warnings-c4800-through-c5999"></a>Avertissements du compilateur C4800 à C5999

Les articles de cette section de la documentation expliquent un sous-ensemble des messages d’avertissement générés par le compilateur.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>Messages d’avertissement

|Warning|Message|
|-------------|------------|
|[Avertissement du compilateur (niveau 4) C4800](compiler-warning-level-3-c4800.md)| Conversion implicite de '*type*» en valeur booléenne. Perte d’informations possible |
|[Avertissement du compilateur (niveau 1) C4803](compiler-warning-level-1-c4803.md)|«*méthode*' : la méthode raise a une classe de stockage différent de celui de l’événement, '*événement*»|
|[Avertissement du compilateur (niveau 1) C4804](compiler-warning-level-1-c4804.md)|«*opération*' : utilisation risquée du type 'bool' dans l’opération|
|[Avertissement du compilateur (niveau 1) C4805](compiler-warning-level-1-c4805.md)|«*opération*' : mélange risqué de type '*type1*'et type'*type2*' dans l’opération|
|[Avertissement du compilateur (niveau 1) C4806](compiler-warning-level-1-c4806.md)|«*opération*' : opération risquée : aucune valeur de type '*type1*'promue en type'*type2*» peut être égal à la constante donnée|
|[Avertissement du compilateur (niveau 1) C4807](compiler-warning-level-1-c4807.md)|«*opération*' : mélange risqué de type '*type1*'et signé le champ de bits de type'*type2*»|
|Avertissement du compilateur (niveau 1) C4808|cas '*valeur*' n'est pas une valeur valide pour la condition switch de type 'bool'|
|Avertissement du compilateur (niveau 1) C4809|switch statement has redundant 'default' label; all possible 'case' labels are given|
|[Avertissement du compilateur (niveau 1) C4810](compiler-warning-level-1-c4810.md)|valeur de pragma pack(show) == n|
|[Avertissement du compilateur (niveau 1) C4811](compiler-warning-level-1-c4811.md)|valeur de pragma conform(forScope, show) == value|
|[Avertissement du compilateur (niveau 1) C4812](compiler-warning-level-1-c4812.md)|style de déclaration obsolète : utilisez '*nouvelle_syntaxe*' à la place|
|[Avertissement du compilateur (niveau 1) C4813](compiler-warning-level-1-c4813.md)|«*fonction*' : une fonction friend d’une classe locale doit avoir été précédemment déclarée|
|[Avertissement du compilateur (niveau 4) C4816](compiler-warning-level-4-c4816.md)|«*param*' : paramètre a un tableau de taille zéro qui sera tronqué (sauf si l’objet est passé par référence)|
|[Avertissement du compilateur (niveau 1) C4817](compiler-warning-level-1-c4817.md)|«*membre*' : utilisation non conforme de '.' pour accéder à ce membre ; compilateur remplacé par '->'|
|[Avertissement du compilateur (niveau 1) C4819](compiler-warning-level-1-c4819.md)|Le fichier contient un caractère qui ne peut pas être représenté dans la page de codes actuelle (numéro). Enregistrez le fichier au format Unicode pour éviter la perte de données|
|[Avertissement du compilateur (niveau 4) C4820](compiler-warning-level-4-c4820.md)|«*octets*'octets de remplissage ajoutés après construction'*member_name*»|
|[Avertissement du compilateur (niveau 1) C4821](compiler-warning-level-1-c4821.md)|Impossible de déterminer le type d’encodage Unicode, enregistrez le fichier avec la signature (BOM)|
|[Avertissement du compilateur (niveau 1) C4822](compiler-warning-level-1-c4822.md)|'member function' : fonction membre de classe locale n’a pas un corps|
|[Avertissement du compilateur (niveau 3) C4823](compiler-warning-level-3-c4823.md)|«*fonction*' : utilise des pointeurs épingle mais déroulement sémantique n’est pas activée. Utilisez /EHa|
|Avertissement du compilateur (niveau 2) C4826|Conversion de '*type1*'en'*type2*' type signe étendu. Cela peut provoquer un comportement inattendu de runtime.|
|Avertissement du compilateur (niveau 3) C4827|Une méthode 'ToString' publique avec 0 paramètre doit être marqué comme étant virtuel et remplacer|
|[Avertissement du compilateur (niveau 1) C4829](compiler-warning-level-1-c4829.md)|Paramètres potentiellement incorrects de la fonction main. Consider 'int main(Platform::Array\<Platform::String^>^ argv)'|
|[Avertissement du compilateur (niveau 1) C4835](compiler-warning-level-1-c4835.md)|«*variable*' : l’initialiseur des données exportées ne sera pas exécuté jusqu'à ce que le code managé pour la première fois dans l’assembly hôte|
|Avertissement du compilateur (niveau 4) C4837|trigraphe détecté : ' ?? *caractère*« remplacé par »*caractère*'|
|[Avertissement du compilateur (niveau 1) C4838](compiler-warning-level-1-c4838.md)|conversion de '*type_1*'en'*type_2*' requiert une conversion restrictive|
|[Avertissement du compilateur (niveau 3) C4839](compiler-warning-level-3-c4839.md)|utilisation non standard de la classe*type*» en tant qu’argument à une fonction variadique|
|[Avertissement du compilateur (niveau 4) C4840](compiler-warning-level-4-c4840.md)|utilisation non portable de la classe*type*» en tant qu’argument à une fonction variadique|
|Avertissement du compilateur (niveau 4) C4841|extension non standard utilisée : désignateur de membre composé utilisé dans offsetof|
|Avertissement du compilateur (niveau 4) C4842|le résultat d '' offsetof' appliqué à un type à l’aide de l’héritage multiple n’est pas garanti pour être cohérente entre les versions du compilateur|
|Avertissement C4843 du compilateur|«*type1*» : Un gestionnaire d’exceptions de référence à un type tableau ou fonction est inaccessible, utilisez '*type2*' à la place|
|Avertissement C4844 du compilateur|' exporter le module *nom_module*; » est désormais la syntaxe préférée pour déclarer une interface de module|
| Avertissement du compilateur (niveau 4) C4845 | «\_\_declspec (non\_init\_all) » est ignorée si ' / d1initall\[0\|1\|2\|3]' n’a pas été spécifié sur la ligne de commande |
| Avertissement du compilateur (niveau 4) C4846 | «*valeur*' n’est pas un argument valide pour ' / d1initall': indicateur de ligne de commande ignorée |
| Avertissement du compilateur (niveau 4) C4847 | «\_\_declspec (non\_init\_all) » peut uniquement être appliqué à une fonction, un type de classe ou une variable locale : ignoré |
| Avertissement du compilateur (niveau 1) C4848 | prise en charge pour l’attribut standard ' aucun\_unique\_adresse dans C ++ 17 et versions antérieures est une extension de fournisseur |
|[Avertissement du compilateur (niveau 4) C4866](c4866.md)| compilateur ne peut pas appliquer l’ordre d’évaluation de gauche à droite pour l’appel à *nom_opérateur*|
|[Avertissement (erreur) C4867](compiler-warning-c4867.md)|'*fonction*' : appel manquant de liste d’arguments de fonction ; utilisez '*appeler*' pour créer un pointeur vers membre|
|[Avertissement du compilateur (niveau 4) C4868](compiler-warning-c4868.md)|«_fichier_(*line_number*) « compilateur ne peut pas appliquer l’ordre d’évaluation de gauche à droite dans la liste d’initialisation entre accolades|
|Avertissement du compilateur (niveau 2) C4872|flottante point de division par zéro détecté lors de la compilation du graphique des appels pour Concurrency::parallel_for_each à l’emplacement : '*emplacement*'|
|Avertissement du compilateur (niveau 1) C4880|conversion de ' const *type_1*'en'*type_2*' : cast d’à partir d’un pointeur ou une référence peut entraîner un comportement non défini dans une fonction restreinte à amp|
|Avertissement du compilateur (niveau 4) C4881|le constructeur et/ou le destructeur ne sera pas appelé pour la variable tile_static '*variable*'|
|Avertissement du compilateur (niveau 1) C4882|passage de foncteurs avec opérateurs d’appels non const à concurrency::parallel_for_each est déconseillé|
|[Avertissement C4900 du compilateur](compiler-warning-level-1-c4900.md)|Incompatibilité de il entre '*tool1*'version'*version1*'et'*tool2*'version'*version2*'|
|[Avertissement du compilateur (niveau 1) C4905](compiler-warning-level-1-c4905.md)|cast de littéral de chaîne étendu en 'LPSTR'|
|[Avertissement du compilateur (niveau 1) C4906](compiler-warning-level-1-c4906.md)|cast de littéral de chaîne en 'LPWSTR'|
|[Avertissement du compilateur (niveau 1) C4910](compiler-warning-level-1-c4910.md)|'\<identificateur > : '__declspec (dllexport)' et 'extern' sont incompatibles sur une instanciation explicite|
|[Avertissement du compilateur (niveau 1) C4912](compiler-warning-level-1-c4912.md)|«*attribut*' : attribut comportement indéfini sur un UDT imbriqué|
|[Avertissement du compilateur (niveau 4) C4913](compiler-warning-level-4-c4913.md)|l'opérateur binaire défini par l'utilisateur ',' existe mais aucune surcharge n'a pu convertir tous les opérandes, opérateur binaire intégré par défaut ',' utilisé|
|Avertissement du compilateur (niveau 1) C4916|pour avoir un dispid, '*description*' : doit être introduites par une interface|
|[Avertissement du compilateur (niveau 1) C4917](compiler-warning-level-1-c4917.md)|«*déclarateur*' : un GUID ne peut être associé à une classe, d’interface ou espace de noms|
|[Avertissement du compilateur (niveau 4) C4918](compiler-warning-level-4-c4918.md)|«*caractère*' : caractère non valide dans la liste d’optimisation pragma|
|[Avertissement du compilateur (niveau 1) C4920](compiler-warning-level-1-c4920.md)|enum enum membre member_1 = value_1 déjà rencontré dans enum enum comme member_2 = value_2|
|Avertissement du compilateur (niveau 3) C4921|«*description*' : valeur de l’attribut '*attribut*' ne doit pas être spécifiée plusieurs fois|
|[Avertissement du compilateur (niveau 1) C4925](compiler-warning-level-1-c4925.md)|«*méthode*' : la méthode dispinterface ne peut pas être appelée à partir du script|
|[Avertissement du compilateur (niveau 1) C4926](compiler-warning-level-1-c4926.md)|«*identificateur*' : symbole déjà défini : attributs ignorés|
|[Avertissement du compilateur (niveau 1) C4927](compiler-warning-level-1-c4927.md)|conversion non conforme ; plusieurs conversions définies par l’utilisateur ont été appliquées implicitement|
|[Avertissement du compilateur (niveau 1) C4928](compiler-warning-level-1-c4928.md)|initialisation de copie non conforme ; plusieurs conversions définies par l'utilisateur ont été appliquées implicitement|
|[Avertissement du compilateur (niveau 1) C4929](compiler-warning-level-1-c4929.md)|«*fichier*' : typelibrary contient une union ; en ignorant le qualificateur 'embedded_idl ' ignoré|
|[Avertissement du compilateur (niveau 1) C4930](compiler-warning-level-1-c4930.md)|«*prototype*' : fonction prototypée non appelée (était une définition de variable souhaitée ?)|
|[Avertissement du compilateur (niveau 4) C4931](compiler-warning-level-4-c4931.md)|bibliothèque de types présumée construite pour des pointeurs 'nombre' bits|
|[Avertissement du compilateur (niveau 4) C4932](compiler-warning-level-4-c4932.md)|__identifier (*identificateur*) et \__identificateur (*identificateur*) ne se distinguent pas|
|Avertissement du compilateur (niveau 1) C4934|'__delegate(multicast)' is deprecated, use '\__delegate' instead|
|[Avertissement du compilateur (niveau 1) C4935](compiler-warning-level-1-c4935.md)|spécificateur d’accès l’assembly modifié à partir de '*accès*»|
|[Avertissement du compilateur (niveau 1, erreur) C4936](compiler-warning-c4936.md)|ce __declspec est pris en charge uniquement lorsqu'il est compilé avec /clr ou /clr:pure|
|[Avertissement du compilateur (niveau 4) C4937](compiler-warning-level-4-c4937.md)|«*text1*'et'*text2*« sont impossibles à distinguer en tant qu’arguments pour »*directive*»|
|[Avertissement du compilateur (niveau 4) C4938](compiler-warning-level-4-c4938.md)|«*var*» : Variable de réduction de la virgule flottante peut entraîner des résultats incohérents sous/fp : strict ou #pragma fenv_access|
|[Avertissement C4939 du compilateur](compiler-warning-level-1-c4939.md)|#pragma vtordisp est déconseillé et sera supprimé dans une version ultérieure de Visual C++|
|[Avertissement du compilateur (niveau 1) C4944](compiler-warning-level-1-c4944.md)|«*symbole*' : ne peut pas importer le symbole de '*assembly1*' : en tant que*symbole*' existe déjà dans la portée actuelle|
|[Avertissement du compilateur (niveau 1) C4945](compiler-warning-level-1-c4945.md)|«*symbole*' : ne peut pas importer le symbole de '*assembly1*' : en tant que*symbole*'a déjà été importé à partir d’un autre assembly'*assembly2* '|
|[Avertissement du compilateur (niveau 1) C4946](compiler-warning-level-1-c4946.md)|reinterpret_cast utilisé entre des classes connexes : '*class1*'et'*classe2*'|
|[Avertissement du compilateur (niveau 1) C4947](compiler-warning-level-1-c4947.md)|«*type_ou_membre*' : marqué comme obsolète|
|[Avertissement du compilateur (niveau 2) C4948](compiler-warning-level-2-c4948.md)|type de retour de '*accesseur*' ne correspond pas au dernier type de paramètre de la méthode setter correspondante|
|[Avertissement du compilateur (niveaux 1 et 4) C4949](compiler-warning-level-1-and-level-4-c4949.md)|les pragmas 'managed' et 'unmanaged' sont significatifs uniquement lors de la compilation avec ' / clr [ : option]'|
|[Avertissement du compilateur (niveau 1, erreur) C4950](compiler-warning-c4950.md)|«*type_ou_membre*' : marqué comme obsolète|
|[Avertissement du compilateur (niveau 1) C4951](compiler-warning-level-1-c4951.md)|«*fonction*' a été modifié depuis les données de profil, données de profil de fonction non utilisées|
|[Avertissement du compilateur (niveau 1) C4952](compiler-warning-level-1-c4952.md)|«*fonction*' : aucune donnée de profil trouvée dans la base de données du programme '*fichier_pgd*»|
|[Avertissement du compilateur (niveau 1) C4953](compiler-warning-level-1-c4953.md)|Inlinee '*fonction*' a été modifié depuis le profil de données ont été collectées, les données de profil non utilisées|
|Avertissement C4954 du compilateur|«*fonction*' : non profilé (contient l’expression de switch __int64)|
|Avertissement C4955 du compilateur|«*importation2*' : importation ignorée ; importation déjà effectuée à partir de '*importation1*»|
|[Avertissement du compilateur (niveau 1, erreur) C4956](compiler-warning-c4956.md)|«*type*' : ce type n’est pas vérifiable|
|[Avertissement du compilateur (niveau 1, erreur) C4957](compiler-warning-c4957.md)|«*cast*' : cast explicite de '*cast_from*'en'*cast_to*' n’est pas vérifiable|
|[Avertissement du compilateur (niveau 1, erreur) C4958](compiler-warning-c4958.md)|«*opération*' : opération arithmétique de pointeur n’est pas vérifiable|
|[Avertissement du compilateur (niveau 1, erreur) C4959](compiler-warning-c4959.md)|Impossible de définir le type non managé '*type*» dans/CLR : safe, car l’accès à ses membres génère du code non vérifiable|
|[Avertissement du compilateur (niveau 4) C4960](compiler-warning-level-4-c4960.md)|«*fonction*' est trop grand pour être profilé|
|[Avertissement du compilateur (niveau 1) C4961](compiler-warning-c4961.md)|Aucune donnée de profil n’a été fusionnée dans 'fichier .pgd', les optimisations guidées par profil sont désactivées|
|[Avertissement du compilateur (niveau 4) C4962](compiler-warning-c4962.md)|«*fonction*» : Optimisations guidées par profil désactivées, car elles génèrent des incohérences au niveau des données de profil|
|Avertissement du compilateur (niveau 1) C4963|«*description*' : aucune donnée de profil trouvée ; les différentes options de compilateur ont été utilisées dans la génération instrumentée|
|[Avertissement du compilateur (niveau 1) C4964](compiler-warning-level-1-c4964.md)|Aucune option d’optimisation a été spécifiée ; informations de profil ne seront pas collectées.|
|[Avertissement du compilateur (niveau 1) C4965](compiler-warning-level-1-c4965.md)|boxing implicite de l’entier 0 ; utilisez nullptr ou cast explicite|
|Avertissement du compilateur (niveau 1) C4966|«*fonction*' a une annotation __code_seg avec un nom de segment non pris en charge, annotation est ignorée|
|Avertissement C4970 du compilateur|constructeur délégué : objet cible ignoré depuis '*type*' est statique|
|Avertissement du compilateur (niveau 1) C4971|Ordre des arguments : \<objet cible >, \<fonction cible > pour un constructeur délégué est déconseillé, utilisez \<fonction cible >, \<objet cible = "« >|
|[Avertissement du compilateur (niveau 1, erreur) C4972](compiler-warning-c4972.md)|La modification ou le traitement direct du résultat d'une conversion unboxing comme lvalue est non vérifiable|
|Avertissement du compilateur (niveau 1) C4973|«*symbole*' : marqué comme déprécié|
|Avertissement du compilateur (niveau 1) C4974|«*symbole*' : marqué comme déprécié|
|Avertissement du compilateur (niveau 3) C4981|Warbird : fonction '*fonction*' marquée comme __forceinline non inline, car elle contient la sémantique d’exceptions|
|Avertissement du compilateur (niveau 3) C4985|nom du symbole ' : attributs absents de la déclaration précédente.|
|[Avertissement C4986](compiler-warning-c4986.md)|«*déclaration*' : spécification d’exception ne correspond pas à la déclaration précédente|
|Avertissement du compilateur (niveau 4) C4987|extension non standard utilisée : 'throw (...)'|
|Avertissement du compilateur (niveau 4) C4988|«*variable*' : variable déclarée en dehors de la portée classe/fonction|
|Avertissement du compilateur (niveau 4) C4989|«*type*' : type a des définitions en conflit.|
|Avertissement du compilateur (niveau 3) C4990|Warbird : *message*|
|Avertissement du compilateur (niveau 3) C4991|Warbird : fonction '*fonction*' marquée comme __forceinline non inline, car le niveau de protection de l’inlinee est supérieur au parent|
|Avertissement du compilateur (niveau 3) C4992|Warbird : fonction '*fonction*' marquée comme __forceinline non inline, car elle contient un assembly inline qui ne peut pas être protégé|
|[Avertissement du compilateur (niveau 3) C4995](compiler-warning-level-3-c4995.md)|«*fonction*' : nom a été marqué comme #pragma deprecated|
|[Avertissement du compilateur (niveau 3) C4996](compiler-warning-level-3-c4996.md)|«*description*' : *message*|
|[Avertissement du compilateur (niveau 1) C4997](compiler-warning-level-1-c4997.md)|«*classe*' : coclasse n’implémente pas une interface COM ou pseudo-interface|
|Avertissement du compilateur (niveau 1) C4998|Échec de l’attente : *attente*(*valeur*)|
|[Avertissement C4999](compiler-warning-level-1-c4999.md)|Avertissement inconnu, choisissez la commande Support technique dans le menu aide de Visual C++ ou ouvrez le fichier d’aide de Support technique pour plus d’informations|
|Avertissement C5022 du compilateur|«*type*' : plusieurs constructeurs de déplacement spécifiés|
|Avertissement C5023 du compilateur|«*type*' : plusieurs opérateurs d’assignation de déplacement spécifiés|
|Avertissement du compilateur (niveau 4) C5024|«*type*' : constructeur de déplacement a été implicitement défini comme étant supprimé|
|Avertissement du compilateur (niveau 4) C5025|«*type*' : déplacement opérateur d’assignation a été implicitement défini comme étant supprimé|
|Avertissement du compilateur (niveaux 1 et 4) C5026|«*type*' : constructeur de déplacement a été implicitement défini comme étant supprimé|
|Avertissement du compilateur (niveaux 1 et 4) C5027|«*type*' : déplacement opérateur d’assignation a été implicitement défini comme étant supprimé|
|Avertissement du compilateur (niveau 1) C5028|«*nom*» : L’alignement spécifié dans la déclaration antérieure (*nombre*) non spécifiée dans la définition|
|Avertissement du compilateur (niveau 4) C5029|extension non standard utilisée : les attributs d’alignement en C++ s’appliquent aux variables, les membres de données et les types de balises uniquement|
|Avertissement du compilateur (niveau 3) C5030|attribut '*attribut*' n’est pas reconnu|
|Avertissement du compilateur (niveau 4) C5031|#pragma warning (pop) : incompatibilité probable, état d’avertissement envoyé dans un autre fichier|
|Avertissement du compilateur (niveau 4) C5032|détecté #pragma warning (push) sans Warning (pop) correspondant #pragma|
|Avertissement du compilateur (niveau 1) C5033|«*classe de stockage*' n’est plus une classe de stockage pris en charge|
|Avertissement C5034 du compilateur|utiliser des intrinsèques '*intrinsèque*' provoque la fonction *fonction* doit être compilé en tant que code invité|
|Avertissement C5035 du compilateur|l’utilisation de fonctionnalité '*fonctionnalité*' provoque la fonction *fonction* doit être compilé en tant que code invité|
|Avertissement du compilateur (niveau 1) C5036|conversion de pointeur de fonction varargs durant la compilation avec /hybrid:x86arm64 '*type1*'en'*type2*'|
|Avertissement du compilateur (erreur) C5037|«*fonction membre*' : une définition hors ligne d’un membre d’un modèle de classe ne peut pas avoir d’arguments par défaut|
|[Avertissement du compilateur (niveau 4) C5038](c5038.md)|membre de données '*member1*'sera initialisé après le membre de données'*member2*'|
|Avertissement du compilateur (niveau 4) C5039|«*fonction*' : pointeur ou référence à une fonction pouvant lever passé à une fonction C externe sous - EHc. Un comportement non défini peut se produire si cette fonction lève une exception.|
|Avertissement du compilateur (niveau 3) C5040|spécifications d’exceptions dynamiques sont valides uniquement dans C ++ 14 et versions antérieures ; traitement en tant que noexcept (false)|
|Avertissement du compilateur (niveau 1) C5041|«*définition*' : définition hors ligne pour le membre de données statique constexpr n’est pas nécessaire et est dépréciée en C ++ 17|
|Avertissement du compilateur (niveau 3) C5042|«*déclaration*' : les déclarations de fonction à portée de bloc ne peut pas être spécifié 'inline' en C++ standard ; supprimez le spécificateur 'inline'|
|Avertissement du compilateur (niveau 2) avertissements C5043|«*spécification*' : spécification d’exception ne correspond pas à la déclaration précédente|
|Avertissement du compilateur (niveau 4) C5044|Un argument pour l’option de ligne de commande *option* pointe vers un chemin d’accès '*chemin d’accès*' qui n’existe pas|
|[Avertissement C5045 du compilateur](c5045.md)|Compilateur va insérer l’atténuation de Spectre pour la charge de mémoire si le commutateur/qspectre spécifié|
|[Avertissement du compilateur (niveau 2) C5046](c5046.md)|«*fonction*» : Symbole impliquant le type avec une liaison interne non définie|
| Avertissement du compilateur (niveau 1) C5047 | utilisation de non standard \_ \_si\_existe avec modules n’est pas pris en charge |
| Avertissement du compilateur (niveau 1) C5048 | Utilisation de macro '*nom_macro*' peut entraîner une sortie non déterministe |
| Avertissement du compilateur (niveau 1) C5049 | «*chaîne*» : Incorporation d’un chemin d’accès complet peut entraîner la sortie de dépend de la machine |
| Avertissement du compilateur (niveau 1) C5050 | Possible de l’environnement incompatible lors de l’importation du module '*nom_module*' : *problème* |
| Avertissement du compilateur (niveau 1) C5100 | \_\_Évaluation des vulnérabilités\_ARGS\_ \_ est réservée pour une utilisation dans les macros variadiques |
| Avertissement du compilateur (niveau 1) C5101 | utilisation de la directive de préprocesseur dans la liste d’arguments de macro de type fonction est un comportement non défini |
| Avertissement du compilateur (niveau 1) C5102 | Ignorer la définition de macro de ligne de commande non valide '*valeur*' |
| Avertissement du compilateur (niveau 1) C5103 | collage '*token1*'et'*token2*' n’entraîne pas un jeton valide de prétraitement |
| Avertissement du compilateur (niveau 1) C5104 | trouvé '*string1*#*string2*« dans la liste de remplacement de macro, voulez-vous utiliser »*string1*» « #*string2*' ? |
| Avertissement du compilateur (niveau 1) C5105 | expansion macro production 'defined' a un comportement indéfini |
| Avertissement du compilateur (niveau 1) C5106 | macro redéfini avec les noms de paramètres différents |
| Avertissement du compilateur (niveau 1) C5107 | final manquant '*char*' caractères |

## <a name="see-also"></a>Voir aussi

[C /C++ compilateur et build erreurs et avertissements des outils](../compiler-errors-1/c-cpp-build-errors.md) \
[Avertissements du compilateur C4000 - C5999](compiler-warnings-c4000-c5999.md)
