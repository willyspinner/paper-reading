# paper-reading
reading papers. Annotations, notes, etc. included

### VGG-FACE

Introduced triplet loss, the idea of minimising euclidean distance between same faces of an identity, and maximising between different identities’ faces (form of ‘metric learning’ - learning by specific loss functions instead of conventional classification losses like cross-entropy / KL).

However, triplet loss is $O(N^2)$ because for each identity, we have to compare it with all the other $N-1$ identities.

### SphereFace A-softmax loss

Introduced angular softmax loss. The idea is to compare the angle between 
feature vector and weight vector to set the decision boundary instead of euclidean distance (e.g. some hyperplane determined by Wx + b). This is better because data is more naturally 'angular' and more discriminative when 
separated via angles.

Also, for FR problems like in VGGFace, this is $O(N)$ instead of $O(N^2)$.

### Orthogonal Deep Feature Decomposition for AIFR (Age Invariant FR)

This involves decomposing a FC feature-vector from a CNN into two components: an age component and an identity component.

The age component is a scalar that is the magnitude of the original feature vec, and x_id is a unit vector (direction is important here).
We use A-softmax loss to make discerning between identities more discriminate (learning the identity-related component).
Used linear regression to learn age-related component. 

More accurate than humans in CACD-VS identification. Scored 99%.
Not really good in open-set, but this is field wide.

### Families in the Wild CNN

Familial relationship verification problem & Family classification problem.
Uses VGGFace as a feature extractor, and then some FCs at the end. Used Triplet loss like VGGFace
to learn family and non-family relations. (Big L2 difference for non-family, small for family).
70% ish for family verification, but 12% for family classification.
