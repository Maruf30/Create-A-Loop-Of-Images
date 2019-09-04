# Create-A-Loop-Of-Images

function catch_that_image() {
  global $post, $posts;
  $first_img = '';
  ob_start();
  ob_end_clean();
  $output = preg_match_all('/<img.+src=['"]([^'"]+)['"].*>/i', $post->post_content, $matches);
  $first_img = $matches [1] [0];
 
  if(empty($first_img)){ //Defines a default image
    $first_img = "/images/default.jpg";
  }
  return $first_img;
}

Note: Don’t forget to define a default image.
Usages:



<?php
if (have_posts()) :
    while (have_posts()) : the_post(); ?>
        <a href="<?php the_permalink();?>" title="<?php the_title(); ?>" class="img-loop">
        <img src="http://media.mediatemple.netdna-cdn.com/wp-content/uploads/images/wordpress-loop-hacks/<?php echo catch_that_image() ?>" alt="<?php the_title(); ?>" />
        </a>
    endwhile;
endif;
?>
