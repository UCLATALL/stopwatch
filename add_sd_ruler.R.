add_sd_ruler <- function(plot, outcome, 
                         legend_x = NULL, legend_y = NULL, 
                         ruler = "show", 
                         legend = "show") {
  # Capture the outcome variable (unquoted)
  outcome_quo <- rlang::enquo(outcome)

  # Try to evaluate outcome inside plot$data, otherwise fall back to global env
  outcome_vals <- tryCatch(
    rlang::eval_tidy(outcome_quo, data = plot$data),
    error = function(e) rlang::eval_tidy(outcome_quo, data = rlang::caller_env())
  )

  # Compute mean and standard deviation of outcome
  m <- mean(outcome_vals, na.rm = TRUE)
  sd_val <- sd(outcome_vals, na.rm = TRUE)

  # If ruler = "show", draw SD segment from mean to mean + 1 SD at y = 0
  if (ruler == "show") {
    segment_df <- data.frame(x = m, xend = m + sd_val, y = 0, yend = 0)
    plot <- plot +
      geom_segment(data = segment_df,
                   aes(x = x, xend = xend, y = y, yend = yend),
                   inherit.aes = FALSE,
                   color = "red", linewidth = 2)
  }

  # If legend = "show" and coordinates are provided, add SD label
  if (legend == "show" && !is.null(legend_x) && !is.null(legend_y)) {
    label_df <- data.frame(
      x = legend_x, 
      y = legend_y,
      label = paste0("SD = ", round(sd_val, 2))
    )
    plot <- plot +
      geom_label(data = label_df,
                 aes(x = x, y = y, label = label),
                 inherit.aes = FALSE,
                 color = "red",
                 fill = NA,
                 label.size = 0.8,
                 label.r = unit(0.15, "lines"),
                 label.padding = unit(0.4, "lines"),
                 fontface = "bold",
                 size = 5)
  }

  return(plot)
}
