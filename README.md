An unhandled exception occurred while processing the request.
JsonException: A possible object cycle was detected. This can either be due to a cycle or if the object depth is larger than the maximum allowed depth of 32. Consider using ReferenceHandler.Preserve on JsonSerializerOptions to support cycles. Path: $.Invitations.Customer.Invitations.Customer.Invitations.Customer.Invitations.Customer.Invitations.Customer.Invitations.Customer.Invitations.Customer.Invitations.Customer.Invitations.Customer.Invitations.Customer.Id.

//Working example
// Principal (parent)
public class Blog
{
    public int Id { get; set; }
    public ICollection<Post> Posts { get; } = new List<Post>(); // Collection navigation containing dependents
}

// Dependent (child)
public class Post
{
    public int Id { get; set; }
    public int BlogId { get; set; } // Required foreign key property
    public Blog Blog { get; set; } = null!; // Required reference navigation to principal
}
