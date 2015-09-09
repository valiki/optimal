In my geophysical work, I rely heavily upon a
generalized inversion algorithm called
Gauss-Newton optimization.  The Gauss-Newton
method minimizes objective functions that can
be iteratively approximated by quadratics.
This approach is particularly appropriate for
least-squares inversions of moderately
non-linear transforms.  The package also
contains code for conjugate-gradient and
line-search optimizations.

Over two decades I have implemented this
package four times, in four different
programming languages.  Every feature of this
package has been motivated by practical
application.  This particular Java version is
only a few years old, but I have already used
it for a dozen or more distinct inversion
problems.  I find no preexisting package so
suitable for typical geophysical inversion
problems.

The abstraction is designed to minimize the
burden of supporting new models, data, and
transforms.  Unlike many approaches, we will
not be required to construct and invert large
linear matrices.  We only need to be able to
perform transformations on specific models
and datasets.  The inversion algorithm need
not know any of the implementation details of
those models and transformations.

For each new problem, I must implement two
distinct Java interfaces.  The data and model
are be encapsulated by two implementations of
the 'Vect' interface.  The simulation
to be inverted must be encapsulated by
'Transform' if non-linear, or by
'LinearTransform' if linear.  Finally,
the model that best explains a particular
dataset is inverted by one of the
'GaussNewtonSolver.solve' methods.
Any constraints or conditioning can be
implemented with one of these interfaces.

Bill Harlan