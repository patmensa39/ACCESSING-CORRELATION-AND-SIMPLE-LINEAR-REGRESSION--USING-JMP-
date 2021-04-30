# ACCESSING-CORRELATION-USING-JMP-
WITH CLEANING DATASET
Graph Builder(
	Size( 1499, 859 ),
	Variables( X( :OD ), Y( :Removal ) ),
	Elements( Points( X, Y, Legend( 10 ) ), Ellipse( X, Y, Legend( 12 ) ) )
)

### Removal vs OD and ID 

Graph Builder(
	Variables( X( :OD ), X( :ID ), Y( :Removal ) ),
	Elements(
		Position( 1, 1 ),
		Points( X, Y, Legend( 5 ) ),
		Ellipse( X, Y, Legend( 7 ), Correlation( 1 ) )
	),
	Elements(
		Position( 2, 1 ),
		Points( X, Y, Legend( 8 ) ),
		Ellipse( X, Y, Legend( 9 ), Correlation( 1 ) )
	)
)



### Fit group 1

Fit Group(
	Bivariate(
		Y( :Removal ),
		X( :OD ),
		Density Ellipse( 0.9, {Line Color( {212, 73, 88} )} ),
		SendToReport(
			Dispatch( {}, "Bivar Plot", FrameBox, {Frame Size( 413, 289 )} ),
			Dispatch(
				{},
				"Bivariate Normal Ellipse P=0.900",
				OutlineBox,
				{Close( 0 )}
			)
		)
	),
	Bivariate(
		Y( :Removal ),
		X( :ID ),
		Density Ellipse( 0.9, {Line Color( {212, 73, 88} )} ),
		SendToReport(
			Dispatch( {}, "Bivar Plot", FrameBox, {Frame Size( 406, 289 )} ),
			Dispatch(
				{},
				"Bivariate Normal Ellipse P=0.900",
				OutlineBox,
				{Close( 0 )}
			)
		)
	),
	<<{Arrange in Rows( 2 )}
)



### Fit group 2

Fit Group(
	Bivariate( Y( :Removal ), X( :OD ), Fit Line( {Line Color( {212, 73, 88} )} ) ),
	Bivariate( Y( :Removal ), X( :ID ), Fit Line( {Line Color( {212, 73, 88} )} ) ),
	<<{Arrange in Rows( 2 )}
)


### scatter matrix

Multivariate(
	Y( :Removal, :OD, :ID, :Width ),
	Estimation Method( "Row-wise" ),
	Scatterplot Matrix( Density Ellipses( 1 ), Fit Line )
)
