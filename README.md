README – Projection MVP NBA 2026
Dans ce projet, j’ai essayé de prédire les résultats du MVP NBA pour la saison 2026 en me basant sur 3 critères (dans l’ordre d’importance, selon moi) :
-	Impact du joueur sur son équipe (45% de l’importance sur le vote final).
o	Comme bien formulé dans le nom du titre, le MVP est le joueur le plus valuable de la saison et donc celui qui a le plus permis à son équipe de gagner. Ce critère vise à ne pas simplement récompenser le meilleur joueur de la meilleure équipe mais bien le joueur qui a le plus permis à son équipe d’être compétitive. 
o	Les statistiques prises en compte concernent le % d’utilisation du joueur, le % de points, passes, rebonds, contres,interceptions par rapport au total de l’équipe ainsi que les résultats de l’équipe avec et sans sa présence sur le terrain.
-	Impact du joueur sur les matchs (30% de l’importance sur le vote final)
o	Depuis des decennies, le MVP NBA figure parmi la crème de la crème des lignes de stats générales et cette année ne fera pas exception. 
o	Les statistiques concernées sont les statistiques de base (Pts, Passes, Rebonds,Interceptions,Contres) ainsi que des statistiques plus avancées permettant de mettre en lumière la domination du joueur sur les matchs (%tir,%3pts,%lancers, volume de tir , statistiques défensives avancées, etc.)
-	Bilan de l’équipe (25% de l’importance sur le vote final)
o	Malgré la domination de chaque joueur, le bilan final de l’équipe reste un facteur essentiel dans les critères d’accès au titre de MVP. Cependant il reste légèrement plus faible que les autres car je souhaite avant tout axer la prédiction vers le joueur le plus valuable et non simplement récompenser le meilleur joueur de la meilleur équipe.

Rentrons dorénavant plus en détail dans le code,
Pour la première partie, on va se consacrer sur l’impact du joueur sur son équipe et émettre différentes catégories plus approfondies afin d’établir un référentiel complet jugeant l’apport du joueur sur son équipe. 
Le VOTT (Value On The Team) représente l’impact direct du joueur sur l’équipe (le % d’utilisation du joueur, le % de points, passes, rebonds, contres,interceptions par rapport au total de l’équipe)
Le VORP (Value Over Replacement Player) représente le nombre de points supplémentaires que l’équipe marque avec tel joueur plutot qu’avec un joueur lambda sur 100 possessions.
Le BPM (Box Plus/Minus) represente le ratio contribution offensive / contribution défensive
Le WS/48 représente le nombre de victoires générées par match afin de mesurer l’importance d’un joueur sur la victoire finale.
Le Rang VORP/BPM/WS48 établit un classement des différents joueurs sur chaque saison par rapport à une caractéristique (VORP/BPM/WS48)



On regroupe ensuite ces critères en fonction de leur importance dans ‘’score_impact’’ afin d’établir un référentiel plus global pour determiner l’impact du joueur sur les performances de son équipe avec dans l’ordre d’importance :
-	VOTT : 40%
-	VORP : 25%
-	BPM : 20%
-	WS48 15%

Nous allons maintenant nous ateler sur la partie plus personnelle pour chaque joueur avec l’étude de ses statistiques d’un point de vue plus global. Comme pour la partie précedente, nous allons établir un score permettant de refléter l’impact du joueur sur la ligue en général. 
Pour cela, nous allons utliser les statistiques plus habituelles pour chaque joueur. Celles-ci sont donc séparer en 5 :
-	PER (Player Effective Rating) fourni dans le dataset initial fournissant un indice global sur les statistiques primaires (points, passes , rebonds , contres et interceptions)
-	TS% ( True Shooting Percentage) réunissant l’efficacité globale du joueur au tir (%2pts, %3pts,%lancers)
-	Usage% (Volume de tir global)
-	Defense avancée : regroupement des statistiques de défense (contres, interceptions) pour mettre en avant les statistiques défensives.
-	AST/TOV : Ratio des passes décissives par rapport aux ballons perdus mettant en avant la qualité du contrôle du ballon.
Afin de créer une donnée de référence pour cette partie. Afin de singulariser les résulats, ils seront « normalisés » soit rapportés sur une échelle allant de 0 à 1.

Enfin pour la troisième partie, nous allons prendre le nombre de victoires pour chaque joueur et la rapporter sur 100 matchs, plus le score sera proche de 100 et plus cette note sera positive.

Nous allons ensuite les reporter sur un indice de MVP regroupant les 3 grandes catégories avec le plus d’importance pour être MVP (Impact sur l’équipe, ligne de stats, bilan de l’équipe) et comparer cela avec les années précedentes et déterminer la proportion des votes pour chaque joueur pour le MVP.
