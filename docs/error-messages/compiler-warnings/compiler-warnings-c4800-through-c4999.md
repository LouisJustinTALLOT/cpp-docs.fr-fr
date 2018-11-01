---
title: Avertissements du compilateur C4800 via C5999
ms.date: 10/24/2018
f1_keywords:
- C4806
- C4807
- C4808
- C4809
- C4810
- C4811
- C4812
- C4813
- C4816
- C4817
- C4822
- C4825
- C4827
- C4837
- C4841
- C4842
- C4843
- C4844
- C4872
- C4880
- C4881
- C4882
- C4900
- C4910
- C4912
- C4913
- C4916
- C4918
- C4920
- C4921
- C4925
- C4926
- C4932
- C4934
- C4935
- C4936
- C4937
- C4938
- C4939
- C4944
- C4947
- C4950
- C4951
- C4952
- C4953
- C4954
- C4955
- C4956
- C4957
- C4958
- C4959
- C4960
- C4961
- C4962
- C4963
- C4966
- C4970
- C4971
- C4972
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
- C4997
- C4998
- C4999
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
ms.openlocfilehash: 672aa1b0e298be3b6754b1706e721ad6798230ec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50642856"
---
# <a name="compiler-warnings-c4800-through-c5999"></a>Avertissements du compilateur C4800 via C5999

Les articles de cette section de la documentation expliquent un sous-ensemble des messages d’avertissement générés par le compilateur.

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>Messages d’avertissement

|Warning|Message|
|-------------|-------------|
|[Avertissement du compilateur (niveau 3) C4800](compiler-warning-level-3-c4800.md)|«*type*' : valeur forcée à bool 'true' ou 'false' (avertissement de performance)|
|[Avertissement du compilateur (niveau 1) C4803](compiler-warning-level-1-c4803.md)|«*méthode*' : la méthode raise a une classe de stockage différent de celui de l’événement, '*événement*»|
|[Avertissement du compilateur (niveau 1) C4804](compiler-warning-level-1-c4804.md)|«*opération*' : utilisation risquée du type 'bool' dans l’opération|
|[Avertissement du compilateur (niveau 1) C4805](compiler-warning-level-1-c4805.md)|«*opération*' : mélange risqué de type '*type1*'et type'*type2*' dans l’opération|
|Avertissement du compilateur (niveau 1) C4806|«*opération*' : opération risquée : aucune valeur de type '*type1*'promue en type'*type2*» peut être égal à la constante donnée|
|Avertissement du compilateur (niveau 1) C4807|«*opération*' : mélange risqué de type '*type1*'et signé le champ de bits de type'*type2*»|
|Avertissement du compilateur (niveau 1) C4808|cas '*valeur*' n'est pas une valeur valide pour la condition switch de type 'bool'|
|Avertissement du compilateur (niveau 1) C4809|l’instruction switch a une étiquette 'default' redondante ; toutes les étiquettes 'case' possibles sont fournies|
|Avertissement du compilateur (niveau 1) C4810|valeur de pragma pack(show) == n|
|Avertissement du compilateur (niveau 1) C4811|valeur de pragma conform(forScope, show) == value|
|Avertissement du compilateur (niveau 1) C4812|style de déclaration obsolète : utilisez '*nouvelle_syntaxe*' à la place|
|Avertissement du compilateur (niveau 1) C4813|«*fonction*' : une fonction friend d’une classe locale doit avoir été précédemment déclarée|
|Avertissement du compilateur (niveau 4) C4816|«*param*' : paramètre a un tableau de taille zéro qui sera tronqué (sauf si l’objet est passé par référence)|
|Avertissement du compilateur (niveau 1) C4817|«*membre*' : utilisation non conforme de '.' pour accéder à ce membre ; compilateur remplacé par '->'|
|[Avertissement du compilateur (niveau 1) C4819](compiler-warning-level-1-c4819.md)|Le fichier contient un caractère qui ne peut pas être représenté dans la page de codes actuelle (numéro). Enregistrez le fichier au format Unicode pour éviter la perte de données|
|[Avertissement du compilateur (niveau 4) C4820](compiler-warning-level-4-c4820.md)|«*octets*'octets de remplissage ajoutés après construction'*member_name*»|
|[Avertissement du compilateur (niveau 1) C4821](compiler-warning-level-1-c4821.md)|Impossible de déterminer le type d’encodage Unicode, enregistrez le fichier avec la signature (BOM)|
|Avertissement du compilateur (niveau 1) C4822|'member function' : fonction membre de classe locale n’a pas un corps|
|[Avertissement du compilateur (niveau 3) C4823](compiler-warning-level-3-c4823.md)|«*fonction*' : utilise des pointeurs épingle mais déroulement sémantique n’est pas activée. Utilisez /EHa|
|Avertissement du compilateur (niveau 2) C4826|Conversion de '*type1*'en'*type2*' type signe étendu. Cela peut provoquer un comportement inattendu de runtime.|
|Avertissement du compilateur (niveau 3) C4827|Une méthode 'ToString' publique avec 0 paramètre doit être marqué comme étant virtuel et remplacer|
|[Avertissement du compilateur (niveau 1) C4829](compiler-warning-level-1-c4829.md)|Paramètres potentiellement incorrects de la fonction main. Considérez ' int main (Platform::Array\<Platform::String ^ > ^ argv)'|
|[Avertissement du compilateur (niveau 1) C4835](compiler-warning-level-1-c4835.md)|«*variable*' : l’initialiseur des données exportées ne sera pas exécuté jusqu'à ce que le code managé pour la première fois dans l’assembly hôte|
|Avertissement du compilateur (niveau 4) C4837|trigraphe détecté : ' ?? *caractère*« remplacé par »*caractère*'|
|[Avertissement du compilateur (niveau 1) C4838](compiler-warning-level-1-c4838.md)|conversion de '*type_1*'en'*type_2*' requiert une conversion restrictive|
|[Avertissement du compilateur (niveau 3) C4839](compiler-warning-level-3-c4839.md)|utilisation non standard de la classe*type*» en tant qu’argument à une fonction variadique|
|[Avertissement du compilateur (niveau 4) C4840](compiler-warning-level-4-c4840.md)|utilisation non portable de la classe*type*» en tant qu’argument à une fonction variadique|
|Avertissement du compilateur (niveau 4) C4841|extension non standard utilisée : désignateur de membre composé utilisé dans offsetof|
|Avertissement du compilateur (niveau 4) C4842|le résultat d '' offsetof' appliqué à un type à l’aide de l’héritage multiple n’est pas garanti pour être cohérente entre les versions du compilateur|
|Avertissement C4843 du compilateur|«*type1*' : un gestionnaire d’exceptions de référence à un type tableau ou fonction est inaccessible, utilisez '*type2*' à la place|
|Avertissement C4844 du compilateur|' exporter le module *nom_module*; » est désormais la syntaxe préférée pour déclarer une interface de module|
|[Avertissement du compilateur (niveau 4) C4866](c4866.md)| compilateur ne peut pas appliquer l’ordre d’évaluation de gauche à droite pour l’appel à *nom_opérateur*|
|[Avertissement (erreur) du compilateur C4867](compiler-warning-c4867.md)|'*fonction*' : appel manquant de liste d’arguments de fonction ; utilisez '*appeler*' pour créer un pointeur vers membre|
|[Avertissement (niveau 4) du compilateur C4868](compiler-warning-c4868.md)|«_fichier_(*line_number*) « compilateur ne peut pas appliquer l’ordre d’évaluation de gauche à droite dans la liste d’initialisation entre accolades|
|Avertissement du compilateur (niveau 2) C4872|flottante point de division par zéro détecté lors de la compilation du graphique des appels pour Concurrency::parallel_for_each à l’emplacement : '*emplacement*'|
|Avertissement du compilateur (niveau 1) C4880|conversion de ' const *type_1*'en'*type_2*' : cast d’à partir d’un pointeur ou une référence peut entraîner un comportement non défini dans une fonction restreinte à amp|
|Avertissement du compilateur (niveau 4) C4881|le constructeur et/ou le destructeur ne sera pas appelé pour la variable tile_static '*variable*'|
|Avertissement du compilateur (niveau 1) C4882|passage de foncteurs avec opérateurs d’appels non const à concurrency::parallel_for_each est déconseillé|
|Avertissement C4900 du compilateur|Incompatibilité de il entre '*tool1*'version'*version1*'et'*tool2*'version'*version2*'|
|[Avertissement du compilateur (niveau 1) C4905](compiler-warning-level-1-c4905.md)|cast de littéral de chaîne étendu en 'LPSTR'|
|[Avertissement du compilateur (niveau 1) C4906](compiler-warning-level-1-c4906.md)|cast de littéral de chaîne en 'LPWSTR'|
|Avertissement du compilateur (niveau 1) C4910|'\<identificateur > : '__declspec (dllexport)' et 'extern' sont incompatibles sur une instanciation explicite|
|Avertissement du compilateur (niveau 1) C4912|«*attribut*' : attribut comportement indéfini sur un UDT imbriqué|
|Avertissement du compilateur (niveau 4) C4913|l'opérateur binaire défini par l'utilisateur ',' existe mais aucune surcharge n'a pu convertir tous les opérandes, opérateur binaire intégré par défaut ',' utilisé|
|Avertissement du compilateur (niveau 1) C4916|pour avoir un dispid, '*description*' : doit être introduites par une interface|
|[Avertissement du compilateur (niveau 1) C4917](compiler-warning-level-1-c4917.md)|«*déclarateur*' : un GUID ne peut être associé à une classe, d’interface ou espace de noms|
|Avertissement du compilateur (niveau 4) C4918|«*caractère*' : caractère non valide dans la liste d’optimisation pragma|
|Avertissement du compilateur (niveau 1) C4920|enum enum membre member_1 = value_1 déjà rencontré dans enum enum comme member_2 = value_2|
|Avertissement du compilateur (niveau 3) C4921|«*description*' : valeur de l’attribut '*attribut*' ne doit pas être spécifiée plusieurs fois|
|Avertissement du compilateur (niveau 1) C4925|«*méthode*' : la méthode dispinterface ne peut pas être appelée à partir du script|
|Avertissement du compilateur (niveau 1) C4926|«*identificateur*' : symbole déjà défini : attributs ignorés|
|[Avertissement du compilateur (niveau 1) C4927](compiler-warning-level-1-c4927.md)|conversion non conforme ; plusieurs conversions définies par l’utilisateur ont été appliquées implicitement|
|[Avertissement du compilateur (niveau 1) C4928](compiler-warning-level-1-c4928.md)|initialisation de copie non conforme ; plusieurs conversions définies par l'utilisateur ont été appliquées implicitement|
|[Avertissement du compilateur (niveau 1) C4929](compiler-warning-level-1-c4929.md)|«*fichier*' : typelibrary contient une union ; en ignorant le qualificateur 'embedded_idl ' ignoré|
|[Avertissement du compilateur (niveau 1) C4930](compiler-warning-level-1-c4930.md)|«*prototype*' : fonction prototypée non appelée (était une définition de variable souhaitée ?)|
|[Avertissement du compilateur (niveau 4) C4931](compiler-warning-level-4-c4931.md)|bibliothèque de types présumée construite pour des pointeurs 'nombre' bits|
|Avertissement du compilateur (niveau 4) C4932|__identifier (*identificateur*) et \__identificateur (*identificateur*) ne se distinguent pas|
|Avertissement du compilateur (niveau 1) C4934|'__delegate (Multicast)' est déconseillé, utilisez '\__delegate' à la place|
|Avertissement du compilateur (niveau 1) C4935|spécificateur d’accès l’assembly modifié à partir de '*accès*»|
|Avertissement du compilateur (niveau 1, erreur) C4936|ce __declspec est pris en charge uniquement lorsqu'il est compilé avec /clr ou /clr:pure|
|Avertissement du compilateur (niveau 4) C4937|«*text1*'et'*text2*« sont impossibles à distinguer en tant qu’arguments pour »*directive*»|
|Avertissement du compilateur (niveau 4) C4938|«*var*' : variable de réduction de la virgule flottante peut entraîner des résultats incohérents sous/fp : strict ou #pragma fenv_access|
|Avertissement C4939 du compilateur|#pragma vtordisp est déconseillé et sera supprimé dans une mise en production ultérieure de Visual C++|
|Avertissement du compilateur (niveau 1) C4944|«*symbole*' : ne peut pas importer le symbole de '*assembly1*' : en tant que*symbole*' existe déjà dans la portée actuelle|
|[Avertissement du compilateur (niveau 1) C4945](compiler-warning-level-1-c4945.md)|«*symbole*' : ne peut pas importer le symbole de '*assembly1*' : en tant que*symbole*'a déjà été importé à partir d’un autre assembly'*assembly2* '|
|[Avertissement du compilateur (niveau 1) C4946](compiler-warning-level-1-c4946.md)|reinterpret_cast utilisé entre des classes connexes : '*class1*'et'*classe2*'|
|Avertissement du compilateur (niveau 1) C4947|«*type_ou_membre*' : marqué comme obsolète|
|[Avertissement du compilateur (niveau 2) C4948](compiler-warning-level-2-c4948.md)|type de retour de '*accesseur*' ne correspond pas au dernier type de paramètre de la méthode setter correspondante|
|[Avertissement du compilateur (niveaux 1 et 4) C4949](compiler-warning-level-1-and-level-4-c4949.md)|les pragmas 'managed' et 'unmanaged' sont significatifs uniquement lors de la compilation avec ' / clr [ : option]'|
|Avertissement du compilateur (niveau 1, erreur) C4950|«*type_ou_membre*' : marqué comme obsolète|
|Avertissement du compilateur (niveau 1) C4951|«*fonction*' a été modifié depuis les données de profil, données de profil de fonction non utilisées|
|Avertissement du compilateur (niveau 1) C4952|«*fonction*' : aucune donnée de profil trouvée dans la base de données du programme '*fichier_pgd*»|
|Avertissement du compilateur (niveau 1) C4953|Inlinee '*fonction*' a été modifié depuis le profil de données ont été collectées, les données de profil non utilisées|
|Avertissement C4954 du compilateur|«*fonction*' : non profilé (contient l’expression de switch __int64)|
|Avertissement C4955 du compilateur|«*importation2*' : importation ignorée ; importation déjà effectuée à partir de '*importation1*»|
|Avertissement du compilateur (niveau 1, erreur) C4956|«*type*' : ce type n’est pas vérifiable|
|Avertissement du compilateur (niveau 1, erreur) C4957|«*cast*' : cast explicite de '*cast_from*'en'*cast_to*' n’est pas vérifiable|
|Avertissement du compilateur (niveau 1, erreur) C4958|«*opération*' : opération arithmétique de pointeur n’est pas vérifiable|
|Avertissement du compilateur (niveau 1, erreur) C4959|Impossible de définir le type non managé '*type*» dans/CLR : safe, car l’accès à ses membres génère du code non vérifiable|
|Avertissement du compilateur (niveau 4) C4960|«*fonction*' est trop grand pour être profilé|
|Avertissement du compilateur (niveau 1) C4961|Aucune donnée de profil n’a été fusionnée dans 'fichier .pgd', les optimisations guidées par profil sont désactivées|
|Avertissement du compilateur (niveau 4) C4962|«*fonction*' : les optimisations guidées par profil désactivées, car elles génèrent des incohérences au niveau des données de profil|
|Avertissement du compilateur (niveau 1) C4963|«*description*' : aucune donnée de profil trouvée ; les différentes options de compilateur ont été utilisées dans la génération instrumentée|
|[Avertissement du compilateur (niveau 1) C4964](compiler-warning-level-1-c4964.md)|Aucune option d’optimisation a été spécifiée ; informations de profil ne seront pas collectées.|
|[Avertissement du compilateur (niveau 1) C4965](compiler-warning-level-1-c4965.md)|boxing implicite de l’entier 0 ; utilisez nullptr ou cast explicite|
|Avertissement du compilateur (niveau 1) C4966|«*fonction*' a une annotation __code_seg avec un nom de segment non pris en charge, annotation est ignorée|
|Avertissement C4970 du compilateur|constructeur délégué : objet cible ignoré depuis '*type*' est statique|
|Avertissement du compilateur (niveau 1) C4971|Ordre des arguments : \<objet cible >, \<fonction cible > pour un constructeur délégué est déconseillé, utilisez \<fonction cible >, \<objet cible = "« >|
|Avertissement du compilateur (niveau 1, erreur) C4972|La modification ou le traitement direct du résultat d'une conversion unboxing comme lvalue est non vérifiable|
|Avertissement du compilateur (niveau 1) C4973|«*symbole*' : marqué comme déprécié|
|Avertissement du compilateur (niveau 1) C4974|«*symbole*' : marqué comme déprécié|
|Avertissement du compilateur (niveau 3) C4981|Warbird : fonction '*fonction*' marquée comme __forceinline non inline, car elle contient la sémantique d’exceptions|
|Avertissement du compilateur (niveau 3) C4985|nom du symbole ' : attributs absents de la déclaration précédente.|
|[Avertissement du compilateur C4986](compiler-warning-c4986.md)|«*déclaration*' : spécification d’exception ne correspond pas à la déclaration précédente|
|Avertissement du compilateur (niveau 4) C4987|extension non standard utilisée : 'throw (...)'|
|Avertissement du compilateur (niveau 4) C4988|«*variable*' : variable déclarée en dehors de la portée classe/fonction|
|Avertissement du compilateur (niveau 4) C4989|«*type*' : type a des définitions en conflit.|
|Avertissement du compilateur (niveau 3) C4990|Warbird : *message*|
|Avertissement du compilateur (niveau 3) C4991|Warbird : fonction '*fonction*' marquée comme __forceinline non inline, car le niveau de protection de l’inlinee est supérieur au parent|
|Avertissement du compilateur (niveau 3) C4992|Warbird : fonction '*fonction*' marquée comme __forceinline non inline, car elle contient un assembly inline qui ne peut pas être protégé|
|[Avertissement du compilateur (niveau 3) C4995](compiler-warning-level-3-c4995.md)|«*fonction*' : nom a été marqué comme #pragma deprecated|
|[Avertissement du compilateur (niveau 3) C4996](compiler-warning-level-3-c4996.md)|«*description*' : *message*|
|Avertissement du compilateur (niveau 1) C4997|«*classe*' : coclasse n’implémente pas une interface COM ou pseudo-interface|
|Avertissement du compilateur (niveau 1) C4998|Échec de l’attente : *attente*(*valeur*)|
|Avertissement C4999|Avertissement inconnu, choisissez la commande Support technique dans le menu aide de Visual C++ ou ouvrez le fichier d’aide de Support technique pour plus d’informations|
|Avertissement C5022 du compilateur|«*type*' : plusieurs constructeurs de déplacement spécifiés|
|Avertissement C5023 du compilateur|«*type*' : plusieurs opérateurs d’assignation de déplacement spécifiés|
|Avertissement du compilateur (niveau 4) C5024|«*type*' : constructeur de déplacement a été implicitement défini comme étant supprimé|
|Avertissement du compilateur (niveau 4) C5025|«*type*' : déplacement opérateur d’assignation a été implicitement défini comme étant supprimé|
|Avertissement du compilateur (niveaux 1 et 4) C5026|«*type*' : constructeur de déplacement a été implicitement défini comme étant supprimé|
|Avertissement du compilateur (niveaux 1 et 4) C5027|«*type*' : déplacement opérateur d’assignation a été implicitement défini comme étant supprimé|
|Avertissement du compilateur (niveau 1) C5028|«*nom*' : alignement spécifié dans la déclaration antérieure (*nombre*) non spécifiée dans la définition|
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
|[Avertissement du compilateur (niveau 2) C5046](c5046.md)|«*fonction*' : symbole impliquant le type avec une liaison interne non définie|
